# VLLM Monitoring with Docker and SSH Tunnel

## 🚀 Launch Instructions

### 1. Start Docker Services

Navigate to the root of the repository and run:

```
docker compose up
```

To run in the background (detached mode), use:

```
docker compose up -d
```

---

### 2. Find the IP Address of the Host Node

On the node where Docker is running, get the IP address with:

```
ip -c a s dev bond0
```

Note the IP address associated with the `bond0` interface.

---

### 3. Set Up an SSH Tunnel from Your Laptop

On your **laptop**, run the following command (replace `<vllm-node-ip>` with the IP address from step 2):

```
ssh -L 13000:<vllm-node-ip>:3000 mlfctl-2
```

This command tunnels port `3000` from the VLLM node to your local port `13000`.

---

### 4. View the Grafana Dashboard

Once the tunnel is active, open your browser and navigate to:

```
http://localhost:13000
```

You should now be able to access the Grafana dashboard.

---

## 🧹 Stopping the Services

To shut down the Docker services, run:

```
docker compose down
```

---
