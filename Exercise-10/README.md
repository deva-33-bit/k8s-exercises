# Exercise 10: Multi-Node Cluster with Multiple Apps and ReplicaSets

A Product Catalog (2 replicas) and a Shopping Cart (3 replicas) run on a 3-node Minikube cluster. Pod anti-affinity forces each replica of an app onto a different node, so the loss of one node doesn't take a service down.

## Files

| File | Purpose |
|---|---|
| `product_catalog.py`, `Dockerfile.product` | Catalog API (`GET /products`) |
| `shopping_cart.py`, `Dockerfile.shopping` | Cart API (`GET` and `POST /cart`) |
| `product_catalog_deployment.yaml` | Deployment, 2 replicas, anti-affinity |
| `shopping_cart_deployment.yaml` | Deployment, 3 replicas, anti-affinity |
| `*_service.yaml` | NodePort Services |
| `item.json` | Sample cart item for the POST test |

## Steps (Windows PowerShell)

1. Start the cluster: `minikube start --nodes 3 -p devops-multinode --driver=docker --memory=2000 --cpus=2`
2. Build: `docker build -t product-catalog:latest -f Dockerfile.product .` and `docker build -t shopping-cart:latest -f Dockerfile.shopping .`
3. Load into every node: `minikube -p devops-multinode image load product-catalog:latest` and the same for `shopping-cart:latest`
4. Deploy: `kubectl apply -f` each Deployment and Service file
5. Check spread: `kubectl get pods -o wide`
6. Access: `minikube -p devops-multinode service <name> --url` (one terminal each)
7. Test with `curl.exe`

![Nodes](../Images/ex10-nodes.png)

![Pods spread across nodes](../Images/ex10-pods.png)

![curl tests](../Images/ex10-curl.png)

## Notes

- `requiredDuringSchedulingIgnoredDuringExecution` anti-affinity on `kubernetes.io/hostname` means no node can hold two pods of the same app. It needs at least as many nodes as replicas.
- `imagePullPolicy: Never` is used because the images exist only on the nodes.
- Each pod keeps its own in-memory cart, so a cart read may hit a different pod. Production apps store state in a shared database.
- The handout's registry add-on and `--force` flag were not needed.

## Cleanup

```
kubectl delete -f .
minikube -p devops-multinode stop
```
