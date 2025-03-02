# Microservices Kubernetes Deployment

## Overview
This guide provides step-by-step instructions for deploying a microservices-based application on Kubernetes using Minikube.

## Prerequisites
Ensure you have the following tools installed:
- **Minikube** (for local Kubernetes cluster)
- **kubectl** (Kubernetes CLI tool)
- **Docker** (for image builds)

## Minikube Setup
1. Start Minikube:
   ```bash
   minikube start
   ```
2. Enable the Ingress controller:
   ```bash
   minikube addons enable ingress
   ```
3. Verify Ingress is running:
   ```bash
   kubectl get pods -n kube-system
   ```

## Deploy Microservices
### Apply Deployments
```bash
kubectl apply -f deployments/user-service.yaml
kubectl apply -f deployments/product-service.yaml
kubectl apply -f deployments/order-service.yaml
kubectl apply -f deployments/gateway-service.yaml
```

### Apply Services
```bash
kubectl apply -f services/user-service.yaml
kubectl apply -f services/product-service.yaml
kubectl apply -f services/order-service.yaml
kubectl apply -f services/gateway-service.yaml
```

### Apply Ingress
```bash
kubectl apply -f ingress/ingress.yaml
```

## Verification
1. Check running pods:
   ```bash
   kubectl get pods
   ```
2. Test services via Ingress:
   ```bash
   curl http://$(minikube ip)/api/users
   curl http://$(minikube ip)/api/products
   curl http://$(minikube ip)/api/orders
   curl http://$(minikube ip)/
   ```

## Troubleshooting
- If pods fail to start, check logs:
  ```bash
  kubectl logs <pod-name>
  ```
- If services are unreachable, check Ingress:
  ```bash
  kubectl get ingress
  ```

## Required File Structure
```
submission/
├── deployments/
│   ├── user-service.yaml
│   ├── product-service.yaml
│   ├── order-service.yaml
│   ├── gateway-service.yaml
├── services/
│   ├── user-service.yaml
│   ├── product-service.yaml
│   ├── order-service.yaml
│   ├── gateway-service.yaml
├── ingress/
│   ├── ingress.yaml
├── README.md
```

## Deliverables
- Kubernetes manifests for Deployments, Services, and Ingress
- README.md with instructions
