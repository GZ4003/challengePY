# PYTHON-APP

## Para empezar a trabajar con este repositorio de GitHub se deben seguir los siguentes pasos:

### 1. Clonar el repositorio:

git clone <URL_DEL_REPOSITORIO>

Una vez en el directorio creamos los ficheros que usaremos en este caso usaremos como microservicio NGINX por lo tanto creamos un Dockerfile y nginx.conf

### 2. Exposición de la aplicación como servicio mediante definición de Docker Compose.

#### Construir la imagen Docker y exponerla con Nginx:

```bash
docker-compose up --build
```
*Abre un navegador web y navega a http://localhost:6969. Deberías ver la aplicación funcionando correctamente.*

### Exposición de la aplicación como servicio mediante definición de Kubernetes.

#### Crear espacio de trabajo
```bash
kubectl create namespace flask
```
#### Crear secreto con la credenciales de Docker Hub 
*Esto se hace para que Kubernetes pueda acceder a imagen a pesar que este publica*
```bash
kubectl create secret -n flask docker-registry flask-image \
    --docker-server=https://index.docker.io/v1/ \
    --docker-username= \
    --docker-password=
```
#### Desplegar la aplicación en Kubernetes:
```bash
helm install flask-deploy . -n flask -f values.yaml  --debug
```
 #### Verificar el estado del despliegue
 Esto mostrará el estado de los pods en tu clúster de Kubernetes. Espera hasta que el pod correspondiente al despliegue esté en estado Running.
 ```bash
kubectl get pods --namespace flask
```
#### Ver el listado de servicios 
 ```bash
kubectl get svc
```
#### Para acceder a la aplicación del cluster de Kubernetes (local)
 ```bash
minikube service flask-deploy-flaskapp-helm-chart -n flask
```
* Se debe seleccionar la segunda IP *
*Con estos pasos, deberías poder levantar la aplicación tanto localmente utilizando Docker como en un clúster de Kubernetes utilizando Helm. Asegúrate de seguir los pasos con cuidado y realizar las configuraciones necesarias según tus requisitos específicos.*



