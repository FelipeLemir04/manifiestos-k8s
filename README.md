Herramientas y tecnologías utilizadas:
Minikube

kubectl

Git y GitHub

Visual Studio Code

Docker

Pasos para realizar el trabaj:
1. Preparar el entorno local
. Crear los directorios
Trabajé con dos repositorios locales:

Uno para el contenido de la página web y otro para los manifiestos de Kubernetes
mkdir sitio-web
mkdir manifiestos-k8s
cd sitio-web
git init
cd ../manifiestos-k8s
git init

Cada uno se debe vincula después con un repositorio público de mi cuenta de GitHub.

2. Obtener el contenido base de la web
Hice un fork del repositorio base

Ingresé a https://github.com/ewojjowe/static-website

Luego, en tu terminal:

git clone https://github.com/FelipeLemir04/static-website sitio-web
cd sitio-web

Luego personalicé el contenido del sitio con Visual Studio Code

git add .
git commit -m "Sitio personalizado"
git push origin main

3. Crear los manifiestos de Kubernetes
En el directorio manifiestos-k8s, creo los archivos YAML para los siguientes recursos:

Deployment
Define cómo se va a desplegar tu contenedor (probablemente con una imagen tipo nginx o httpd).

Service
Exponé la aplicación para que se pueda acceder desde el navegador.

PersistentVolume y PersistentVolumeClaim
Para que el contenido personalizado no se pierda aunque se reinicie el pod.

4. Aplicar los manifiestos
kubectl apply -f pvc.yaml
kubectl apply -f pv.yaml
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml

5. Verificar funcionamiento
kubectl get pv
kubectl get pvc

6. Iniciar página
minikube service sitio-web-service
