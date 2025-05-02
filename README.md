# k8s-hpa-node-monitoring
🚀 Kubernetes Monitoring &amp; Auto Scaling (HPA + DaemonSet)

# 🚀 Kubernetes Monitoring & Auto Scaling (HPA + DaemonSet)

This project demonstrates the power of **Kubernetes Horizontal Pod Autoscaler (HPA)** and **DaemonSet** in optimizing system **resources, cost, and time**. It sets up a load-balanced PHP-Apache deployment with auto-scaling and node-level monitoring using Prometheus Node Exporter.

---

## 🧠 Concepts Covered

- 📈 **HPA (Horizontal Pod Autoscaler)**
  - Automatically scales pods based on CPU usage.
  - Keeps applications responsive and cost-efficient.
- 🔄 **DaemonSet**
  - Ensures that a pod runs on **every node** in the cluster.
  - Perfect for agents like Prometheus Node Exporter.

---

## 📂 Files Included

- `php-apache-deployment.yaml` – Deploys and exposes a sample app.
- `hpa.yaml` – Configures autoscaling using CPU metrics.
- `daemonset-node-exporter.yaml` – Deploys Node Exporter on each node.
- ⚙️ Instructions for setting up `metrics-server` and generating load.

---

## 🛠 How to Run

```bash
# 1. Deploy the app
kubectl apply -f php-apache-deployment.yaml

# 2. Install metrics server
kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/high-availability-1.21+.yaml

# 3. Apply HPA
kubectl apply -f hpa.yaml

# 4. Generate load (separate terminal)
kubectl run -i --tty load-generator --rm --image=busybox:1.28 --restart=Never -- /bin/sh -c "while sleep 0.01; do wget -q -O- http://php-apache; done"

# 5. Apply DaemonSet
kubectl apply -f daemonset-node-exporter.yaml
