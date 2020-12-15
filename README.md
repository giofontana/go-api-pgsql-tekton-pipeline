# go-api-pgsql-tekton-pipeline


> oc new-project go-api-pgsql-tekton-cicd
Now using project "go-api-pgsql-tekton-cicd" on server "https://api.ocp.rhbr-consulting.com:6443".

You can add applications to this project with the 'new-app' command. For example, try:

    oc new-app ruby~https://github.com/sclorg/ruby-ex.git

to build a new example application in Python. Or use kubectl to deploy a simple Kubernetes application:

    kubectl create deployment hello-node --image=gcr.io/hello-minikube-zero-install/hello-node

>  oc get serviceaccount pipeline
NAME       SECRETS   AGE
pipeline   2         23s

> oc create -f k8s/pipeline-pvc.yaml
persistentvolumeclaim/source-pvc created

> oc apply -f tasks/01_create_namespaces.yaml
task.tekton.dev/create-namespaces created

> oc apply -f tasks/02_build_from_source.yaml
task.tekton.dev/build-from-source created

> oc apply -f pipeline.yaml
pipeline.tekton.dev/build-go-api-pgsql created

> oc adm policy add-cluster-role-to-user cluster-admin system:serviceaccount:go-api-pgsql-tekton-cicd:pipeline
clusterrole.rbac.authorization.k8s.io/cluster-admin added: "system:serviceaccount:go-api-pgsql-tekton-cicd:pipeline"

https://www.openshift.com/blog/guide-to-openshift-pipelines-part-1-introducing-openshift-pipelines

TODO:
- 