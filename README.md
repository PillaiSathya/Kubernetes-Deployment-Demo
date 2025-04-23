# Kubernetes Deployment - NGINX Deployment Demo

## ✨ Overview
This demo showcases how to create a **Kubernetes Deployment** that manages multiple replicas of an NGINX web server.

---

## 🖊️ YAML Configuration: `nginx-deployment.yaml`
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx
        ports:
        - containerPort: 80
```

### Explanation:
- **replicas: 3**: Ensures 3 pods are always running.
- **selector**: Matches the label `app: nginx` to group the pods.
- **template**: Defines the pod structure, including the NGINX container.

---

## ⚙️ Commands Used
```bash
# Create the deployment
kubectl apply -f nginx-deployment.yaml

# View the pods created
kubectl get pods

# Expose the deployment to create a service
kubectl expose deployment nginx-deployment --port=80 --type=NodePort

# View the service and access port
kubectl get svc
```

---

## 🌐 Access the Application
After exposing the deployment, you'll get a **NodePort** like:
```txt
80:31204/TCP
```
You can access NGINX in the browser at:
```
http://127.0.0.1:31204
```

---

## 🚀 Benefits of Deployment
- Easy scaling (change `replicas` value).
- Automatic self-healing of pods.
- Controlled rolling updates and rollbacks.

---

## 📷 Screenshot
Include a screenshot of the browser displaying the NGINX welcome page via `http://127.0.0.1:<NodePort>`.
![ReplicaSet Screenshot](screenshot.png)

---

## 📁 Files in this Project
- `nginx-deployment.yaml`
- `README.md`
- (optional) `screenshot.png`

---

## 🌟 Author
**Sathya**  
DevOps Enthusiast | Docker & Kubernetes Learner

---

## 🔗 GitHub
[GitHub Repository →](https://github.com/PillaiSathya/Kubernetes-Deployment-Demo)

---

## 📊 Next Topics
- Kubernetes Rolling Updates
- Kubernetes Services (ClusterIP vs NodePort vs LoadBalancer)
- Helm Charts

---

Let's deploy like a pro! 🤩

