## Deploy Sock Shop Sample Application

### Deploy SockShop
1. On the EKS Bastion Host deploy sockshop
  ```
  cd k8s-apps
  ./deploy-sockshop.sh
  ```

### Validate SockShop Dev instance
1. List all objects
  ```
   kubectl get all -n dev
  ```

  ![SockShopDevRunning](../assets/images/sockshopdev.png)

2. Wait a couple of minutes until all the pods are Ready and Running and the LoadBalancer objects have EXTERNAL-IPs
  ![SockShopDevRunning](../assets/images/sockshopdevrun.png)  

3. Validate the Dev instance
   - Use the External IP of service/front-end and port 8080  
   ![SockShopDevWeb](../assets/images/sockshopdevweb.png)  
   - Register an account
   - Browse the items
   - Add an item to your cart

### Validate SockShop Production instance
1. List all objects
  ```
  kubectl get all -n production
  ```

 ![SockShopDevRunning](../assets/images/sockshopdev.png)

2. Wait a couple of minutes until all the pods are Ready and Running and the LoadBalancer objects have EXTERNAL-IPs
 ![SockShopDevRunning](../assets/images/sockshopdevrun.png)  

3. Validate the Dev instance
  - Use the External IP of service/front-end and port 8080  
  ![SockShopDevWeb](../assets/images/sockshopdevweb.png)  
  - Register an account
  - Browse the items
  - Add an item to your cart
