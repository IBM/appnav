# Import WebSphere Application Server Network Deployment cells

Importing an existing WebSphere® Application Server Network Deployment cell creates a WAS-ND-Cell Kubernetes custom resource to 
represent the cell. The Application Navigator automatically discovers enterprise applications that are deployed on the cell and creates WAS-Traditional-App Kubernetes custom resources to represent those applications. Application 
Navigator periodically polls the cell to keep the state of the WAS-ND-Cell resources and WAS-Traditional-App resources 
synchronized with the cell.

## About this task

You can import an existing WebSphere Application Server Network Deployment cell into IBM Application Navigator to establish 
visibility and access to the Network Deployment cell. A cell can be imported into Application Navigator with the 'WAS ND Cells'  page in Application Navigator or the Kubernetes **kubectl** command.

## Procedure

### Import the WebSphere Application Server Network Deployment cell by using the 'WAS ND Cells' page

  1. Open the WebSphere Application Server Network Deployment cell page and launch **create dialog**.

     ![](images/importcell.1.png?raw=true)

  1. Enter details and create the cell.

     1. Under the **General** details tab, enter a name for the cell.

        ![](images/importcell.2.png?raw=true)

     1. Click **Endpoints** and enter your host name, and adjust any port values (defaults are provided).

        ![](images/importcell.3.png?raw=true)

     1. Click Credentials and enter a Kubernetes secret name, user name, and password to log in to your cell.

         ![](images/importcell.4.png?raw=true)

     1. Click the **Create** button to create your credentials secret.

        > **Attention:** You can create a new Kubernetes secret or choose an existing one. For a new one, the user name and 
        password you specify is stored as base 64 encoded values in the secret.

  1. Optional: Inspect the cell.

     1. Click cell name to see the detail view.

        ![](images/importcell.5.png?raw=true)

     1. Use the detail view to see cell details.

        ![](images/importcell.6.png?raw=true)


### Import the WebSphere Application Server Network Deployment by using the Kubernetes command-line tool

1.	Create the WebSphere Application Server Network Deployment cell resource.
    1. All fields that are shown are required.
    1. Credentials are a Kubernetes secret in the same namespace.
    1. Interval is the controller polling interval for syncing cells with Kubernetes resources.
    1. Create the cell.yaml file:

       ```
       apiVersion: prism.io/v1beta1
       kind: WAS-ND-Cell
       metadata:
          name: prism-testcell1
          namespace: default
       spec:
          console_url: https://prism-wasnd-dmgr.rtp.raleigh.ibm.com:9043/ibm/console
          credentials: prism-testcell1-secret
          host: prism-wasnd-dmgr.rtp.raleigh.ibm.com
          interval: 30
          soap_port: 8879
       ```

    1. Create the resource with the following command:

       ```
       kubectl create -f cell.yaml
       ```
    
1. Create the secret for the cell credentials.
   1. The user name and password fields must be base 64 encoded.
   1. The secret must be in the same namespace as the corresponding cell.
   1. Create the secret.yaml file.

      ```
      apiVersion: v1
      data:
         password: dGVzdHVzZXJwd2Q=
         username: dGVzdHVzZXI=
      kind: Secret
      metadata:
         name: prism-testcell1-secret
         namespace: default
      ```

   1. Create the resource with the following command:

      ```
      kubectl create -f secret.yaml
      ```
   
1.	Inspect twas-apps resources.

    Use the following commands to see your cell and its secret in the yaml format:

    ```
    kubectl get twas-cell prism-testcell -o yaml
    kubectl get twas-apps -o yaml
    kubectl get secret prism-testcell1-secret -o yaml
    ```

## Results

You get a WAS-ND-Cell Kubernetes resource that represents your WebSphere Application Server Network Deployment cell and 
one WAS-Traditional-App Kubernetes resource for each enterprise application deployed to that cell.

