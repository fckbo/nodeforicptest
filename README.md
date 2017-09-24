# Node.js Hello World Sample App to test Helm Charts and deployment on icp

This application demonstrates a simple, reusable Node.js web application based on the Express framework.

## Run the app locally

1.[Install Node.js][]

2.Build, run & test your image
+ cd into this project's root directory
+ Run `npm install` to install the app's dependencies
+ Run `npm start` to start the app
+ Access the running app in a browser at <http://localhost:6002>

[Install Node.js]: https://nodejs.org/en/download/

## Run the app locally using docker

1.[Install docker][]

2.Build, run & test your image
+ cd into this project's root directory
+ Run `docker build -t <imagename> .` to create a docker image 
+ Run `docker run -p 7000:6002 -d <imagename>` to start the app

+ alternatively you can directly run 'docker run -p 7000:6002 -d frck/nodeforicptest'

+ Access the running app in a browser at <http://localhost:7000>

[Install docker]: https://docs.docker.com/engine/installation/

## Run the app on a kubernetes cluster (tested with IBM Cloud Private 2.1 Beta 2)

1.[Install an IBM Cloud Private somewhere ][]

2.[Install kubectl][]

3.Connect to your Kubernetes cluster:
+    -kubectl config set-cluster mycluster.icp --server=https://$YOUR-CLUSTER-IP:$YOUR-PORT --insecure-skip-tls-verify=true
+    -kubectl config set-context mycluster.icp-context --cluster=mycluster.icp
+    -kubectl config set-credentials mycluster.icp-user --token=<<<<YOUR TOKER HERE>>>
+    -kubectl config set-context mycluster.icp-context --user=mycluster.icp-user --namespace=default
+    -kubectl config use-context mycluster.icp-context

+ Check you can access your cluster
+    -kubectl get pods


+ Deploy with kubectl commands
+    -kubectl create -f k8s-deployment.yaml
+    -kubectl create -f k8s-service.yaml

+or Deploy with helm
+    -helm init --client-only
+    -helm version (check that client matches Tiller server version)
+    -helm install --dry-run --debug ./nodeforicptest-chart
+    -helm install  --debug ./nodeforicptest-chart


+ Access the running app in a browser at <http://YOU-PROXY-ADDRESS:YOUR-SERVICE-PORT>
+    -YOU-SERVICE-PORT can be viewed in the ICP console in the Workloads->Services view
+        or by looking in the k8s-service.yaml or ./nodeforicptest-chart/values.yaml depending on the method used to deploy the app

4.Deploy your app
+ cd into this project's root directory
+   -kubectl create -f k8s-deployment.yaml
+   -kubectl create -f k8s-service.yaml

+ Access the running app in a browser at <http://YOU-CLUSTER-PROXY-IP:YOUR-SERVICE-PORT>
+        or by looking in the k8s-service.yaml or ./nodeforicptest-chart/values.yaml depending on the method used to deploy the app

[Install an IBM Cloud Private somewhere ]: https://www.ibm.com/support/knowledgecenter/en/SSBS6K
[Install kubectl]: https://kubernetes.io/docs/tasks/tools/install-kubectl/  
