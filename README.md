# PYTHON-APP
1-Clonar el repositorio:

git clone <URL_DEL_REPOSITORIO>
cd <NOMBRE_DEL_DIRECTORIO>

2-Construir la imagen Docker:

```bash
docker build -t flaskapp .
```

3-Ejecutar el contenedor Docker localmente:

*docker run -p 6969:6969 flaskapp*

4-Ahora vemos si funciona la imagen yendo al puerto que colocamos antes 

*Abre un navegador web y navega a http://localhost:6969. Deberías ver la aplicación funcionando correctamente.*

# AHORA TOCA KUBERNETES

5-Preparar el archivo values.yaml:

*Edita el archivo values.yaml según tus preferencias y configuraciones específicas del clúster de Kubernetes.*

6-Crear namespace de trabajo

*kubectl create namespace flask 6*

7-Desplegar la aplicación en Kubernetes:

*helm install flaskapp-deploy . -n flask -f values.yaml  --debug*

8-Verificar el estado del despliegue:

*kubectl get pods --namespace flask*


*Esto mostrará el estado de los pods en tu clúster de Kubernetes. Espera hasta que el pod correspondiente al despliegue esté en estado Running.*

9-Para actualizar

helm upgrade flaskapp-deploy . -n flask -f values.yaml  --debug

10-Secreto para docker

kubectl create secret -n flask docker-registry flask \
    --docker-server=https://index.docker.io/v1/ \
    --docker-username=prasadhole \
    --docker-password=Prasad@2002

11-Acceder a la aplicación en Kubernetes:

kubectl get svc

*Utiliza la dirección IP y el puerto para acceder a la aplicación en el navegador web.*

*Con estos pasos, deberías poder levantar la aplicación tanto localmente utilizando Docker como en un clúster de Kubernetes utilizando Helm. Asegúrate de seguir los pasos con cuidado y realizar las configuraciones necesarias según tus requisitos específicos.*




