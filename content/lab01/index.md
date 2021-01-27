## Instrumenting Kubernetes with Dynatrace

In this exercise we will install the Dynatrace Operator.


### 1. Deploy Dynatrace

1. In Dynatrace tenant select "Deploy"

   ![Deploy](../../assets/images/deploydynatrace.png)

2. Search for kubernetes
   ![SearchForK8S](../../assets/images/searchk8s.png)

3. Click on Kubernetes tile from above
   ![DeployK8S](../../assets/images/deployk8s-full.png)

4. Click on Monitor Kubernetes
   ![SearchForK8S](../../assets/images/monitork8s.png)

5. Click Create PaaS token

   ![CreatePaasToken](../../assets/images/createpaastoken.png)

   - After creating the PaaS token follow the step 1-3 above to get back to this screen.

6. Create API token

   ![CreateAPIToken](../../assets/images/createapitoken.png)

   - Make sure you have the "Access problem and event feed, metrics, and topology", "Read Configuration" and "Write Configuration" settings enabled for the API token.

   ![CreateAPIToken](../../assets/images/apitoken.png)

   -After creating the PaaS token follow the step 1-3 above to get back to this screen.

7. Select the PaaS and API tokens you created above

   ![SelectTokens](../../assets/images/selecttokens.png)

8. Click the Copy Button

   ![CopyScript](../../assets/images/copyscript.png)

9. Run Script on Bastion host

   ![RunScript](../../assets/images/runscript1.png)
   ![RunScript](../../assets/images/runscript2.png)


### 2. Update Kubernetes Integration Settings
1. In Dynatrace Tenant, Click Settings -> Cloud and Virtualization -> Kubernetes

   ![K8SConfig](../../assets/images/k8sconfig.png)


2. Click on the Edit icon for the configured K8S clustername

  ![ClusterEdit](../../assets/images/clusteredit.png)       


3. Set the toggle switches
   - Toggle off "Require valid certificates for communication with API server". This is because the workshop k8s cluster are using self signed certificates.

   - Toggle on "Monitor Prometheus exports"
   ![K8SToggles](../../assets/images/k8stoggles.png)

4. Click Add event field selector
   ![K8SEventSelector](../../assets/images/addevent.png)

5. Add a field selector name and expression

   ![K8SEventSelector](../../assets/images/nonnodeevent.png)

   - Field selector
   ```
   involvedObject.kind!=Node
   ```

   - Click Save.

6.  Toggle on Monitor events

   ![K8SMonitorEvents](../../assets/images/monitorevents.png)

7. Click Save.   
