# KubeKommander
KubeKommander: A comprehensive educational repository that serves as a guiding compass, unraveling the complexities of Kubernetes with detailed examples, step-by-step tutorials, and invaluable insights to empower you in mastering the art of cluster management and orchestration.


```markdown
# KubeKommander

Welcome to KubeKommander! This repository serves as a documentation of my journey and learnings in the world of Kubernetes. Here, you will find various commands, deployment manifests, and explanations to help you navigate through the Kubernetes ecosystem.

## Kubernetes Components

### Default Namespaces
- `default`: The default namespace where objects are created if no other namespace is specified.
- `kube-system`: Namespace for Kubernetes system components and other essential resources.
- `kube-public`: Read-only namespace accessible by all users, including unauthenticated users.
- `kube-node-lease`: Namespace containing node lease objects to improve cluster stability.

## Commands

### Basic Commands

#### `kubectl get pods`
- Syntax: `kubectl get pods`
- Example: `kubectl get pods -n default`
- Imperative command
- Explanation: This command lists all pods in the current namespace.

#### `kubectl get deployments`
- Syntax: `kubectl get deployments`
- Example: `kubectl get deployments -n default`
- Imperative command
- Explanation: This command lists all deployments in the current namespace.

#### `kubectl create`
- Syntax: `kubectl create [resource]`
- Example: `kubectl create -f deployment-manifests.yml`
- Imperative command
- Explanation: This command creates a resource from a file or standard input.

#### `kubectl delete`
- Syntax: `kubectl delete [resource]`
- Example: `kubectl delete deployment sample-deployment`
- Imperative command
- Explanation: This command deletes resources by filenames, filenames with wildcard, or resources specified in a YAML/JSON file.

#### `kubectl apply`
- Syntax: `kubectl apply -f [resource]`
- Example: `kubectl apply -f deployment-manifests.yml`
- Imperative command
- Explanation: This command applies changes to resources by filename, filenames with wildcard, or resources specified in a YAML/JSON file.

### Advanced Commands

#### `kubectl scale`
- Syntax: `kubectl scale --replicas=[number] [resource]`
- Example: `kubectl scale --replicas=5 deployment/sample-deployment`
- Imperative command
- Explanation: This command scales the number of replicas in a deployment, replica set, or stateful set.

#### `kubectl rollout`
- Syntax: `kubectl rollout [command] [resource]`
- Example: `kubectl rollout status deployment/sample-deployment`
- Imperative command
- Explanation: This command manages rollouts of a deployment.

#### `kubectl logs`
- Syntax: `kubectl logs [pod]`
- Example: `kubectl logs sample-pod`
- Imperative command
- Explanation: This command prints the logs for a pod or container.

#### `kubectl exec`
- Syntax: `kubectl exec [pod] [command]`
- Example: `kubectl exec sample-pod -- ls /app`
- Imperative command
- Explanation: This command executes a command in a container.

## Sample Manifests
```
### Deployment Manifest (deployment-manifests.yml)
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: sample-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: sample-app
  template:
    metadata:
      labels:
        app: sample-app
    spec:
      containers:
      - name: sample-container
        image: nginx:latest
        ports:
        - containerPort: 80
```

### Pod Definition (pod-definition.yml)
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: sample-pod
spec:
  containers:
  - name: sample-container
    image: nginx:latest
    ports:
    - containerPort: 80
```

### Service (services.yml)
```yaml
apiVersion: v1
kind: Service
metadata:
  name: sample-service
spec:
  selector:
    app: sample-app
  ports:
  - protocol: TCP
    port: 80
    targetPort: 80
```

### Ingress (ingress.yml)
```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: sample-ingress
spec:
  rules:
  - host: example.com
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: sample-service
            port:
              number: 80
```

> Note: The above manifests are just samples and should be customized as per your requirements.


A "dry run" command is typically used to simulate the execution of a command without actually making any changes to the system. In the context of Kubernetes, you can use the `--dry-run` flag with the `kubectl create` and `kubectl apply` commands to see what changes would be made without actually applying them. For example:

```shell
kubectl create -f deployment-manifests.yml --dry-run=client
```

This command will validate the YAML file and provide output indicating whether it is valid or not, without creating any resources. The `--dry-run=client` flag specifies that the dry run should be performed on the client side without making any server-side changes.

The dry run command is useful for verifying the correctness of your YAML files and ensuring that the desired changes are as expected before actually applying them to your Kubernetes cluster.

Best wishes on your Kubernetes exploration! 🚀

Sources:
- Kubernetes Documentation: https://kubernetes.io/docs/ 

## Disclaimer

This repository is part of my personal learning journey in Kubernetes and serves as a documentation of my learnings. The content and examples provided here are prepared by me and may not represent best practices or production-ready configurations.

## Note

If you find this repository helpful, I kindly request you to share it on LinkedIn and Twitter, and tag me: Satish Sutar.
