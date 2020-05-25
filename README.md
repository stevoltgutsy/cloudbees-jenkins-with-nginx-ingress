# cloudbees-jenkins-with-nginx-ingress


I used Helm 3 for this demonstration in KVM platform 

helm repo add cloudbees https://charts.cloudbees.com/public/cloudbees
helm repo update
helm search repo jenkins

helm inspect values stable/jenkins > /tmp/jenkins.values

add storageclass: < name of your storage class to enable persistent voluem creation for Jenkins>

run your helm chart command to install Jenkins on your Kubernetes bare-metal running on KVM or Virtualbox(via vagrant).

helm install cloudbees-jenkins-distribution  cloudbees/cloudbees-jenkins-distribution --set nginx-ingress.enabled=true -f /tmp/jenkins.values --namespace=cloudbees-jenkins-distribution
