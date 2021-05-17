# Kubernetes

## Namespaces

Plantilla para crear un namespace, namespace.yaml

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: ejemplo_namespace
```

- **kubectl get namespaces:** Lista los namespaces
- **kubectl create namespace \[namespace_name\]:** Crear un nuevo namespace
- **kubectl apply -f \[namespace.yaml\]:** Crea un namespace a partir de una plantilla
- **kubectl delete namespace \[namespace_name\]:** Elimina un nacespace por su nombre
- **kubectl delete -f \[namespace.yaml\]:** Eliminar un nacespace a partir de una plantilla

## Pods

Plantilla para crear un pod, pod.yaml

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: wildfly
spec:
  containers:
  - name: wildfly
    image: jboss/wildfly
```

- **kubectl get pods:** Muestra el listado de pods
- **kubectl apply -f \[pod.yaml\]:** Crea un pod a partir de la plantilla
- **kybectl exec -it \[pod_name\]\[cmd\]:** Execute the given command in a running pod
- **kubectl logs \[pod_name\]:** Print out logs from the given pod
- **kubectl delete pod \[pod_name\]:** Deletes the given pod
- **kubectl apply -f \[config_file_name\]:** Tells cubernetes to process the config
- **kubectl describe pod \[pod_name\]:** Print out some information about the running pod

### Deployment Commands

- **kubectl get deployments:** List all the running deployments
- **kubectl describe deployment \[deployment_name\]:** Print out details about a specific deployment
- **kubectl apply -f \[config_file_name\]:** Create a deployment out of a config file
- **kubectl delete deployment \[deployment_name\]:** Delete a deployment
- **kubectl rollout restart deployment \[deployment_name\]:** Updating the image used by a deployment

- **kubectl create secret generic jwt-secret --from-literal=JWT_KEY=\<hash_secret\>:** Generar un JWT_SECRET generico