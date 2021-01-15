

## Exercise 1: Instrumenting K8S with the OneAgent

In this exercise we will install the Dynatrace Operator for K8S utlizing a Helm Chart.

### 1. Install Helm 3 (reference: https://docs.aws.amazon.com/eks/latest/userguide/helm.html)

On your Bastion Host run the following command:
~~~~
  curl -sSL https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash
~~~~
  ![InstallHelm](assets/images/installhelm.png)

### 2. Deploy Dynatrace Operator

1. In Dynatrace tenant select "Deploy"
  ![Deploy](assets/images/deploydynatrace.png)
   
2. Search for kubernetes
  ![SearchForK8S](assets/images/searchk8s.png)

3. Click on Kubernetes tile from above
  ![DeployK8S](assets/images/deployk8s-full.png)

4. Click Create PaaS token
  ![CreatePaasToken](assets/images/createpaastoken.png)

After creating the PaaS token follow the step 1-3 above to get back to this screen.

5. Create API token
  ![CreateAPIToken](assets/images/createapitoken.png)

After creating the PaaS token follow the step 1-3 above to get back to this screen.

6. Select the PaaS and API tokens you created above
  ![SelectTokens](assets/images/selecttokens.png)

7. Add the OneAgent Helm Repository

On your EKS Bastion Host run:
~~~~
  helm repo add dynatrace https://raw.githubusercontent.com/Dynatrace/helm-charts/master/repos/stable
~~~~

  ![AddDyantraceRepo](assets/images/addhelmrepo.png)


8. Create the K8S dynatrace namespace

On your EKS Bastion Host run:
~~~~
  kubectl create namespace dynatrace
~~~~

  ![CreateNamespace](assets/images/createnamespace.png)
 
9. In the Dynatrace Deploy Kubernetes screen: Click "Copy" to copy the values.yaml content and paste that into a new file on your Bastion host

  ![CopyValues](assets/images/copyvalues.png)

10. Deploy the Oneagnet on Kubernetes

On your EKS Bastion Host run:
~~~~
helm install dynatrace-oneagent-operator dynatrace/dynatrace-oneagent-operator -n dynatrace --values values.yaml
~~~~

  ![InstallOneAgent](assets/images/installoneagent.png)

### 3. Validate Install

Run the kubectl commands in the screenshot above.
