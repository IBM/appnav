# Import WAS ND Cell  

Importing a WebSphere® Application Server Network Deployment cell creates a WAS-ND-Cell Kubernetes custom resource to 
represent the collective. The WAS-ND-Cell automatically discovers enterprise applications that are deployed on the collective.
The WAS-ND-Cell also creates WAS-Traditional-App Kubernetes custom resources to represent those applications. Application 
Navigator periodically polls the cell to keep the state of the WAS-ND-Cell resources and WAS-Traditional-App resources 
synchronized with the cell.

## About this task

You can import a WebSphere Application Server Network Deployment cell into an IBM Application Navigator cell to establish 
visibility and access to the Network Deployment cell. A WebSphere Application Server Network Deployment cell can be imported 
into Application Navigator with the WAS-ND-Cell list view page in Application Navigator or the Kubernetes kubectl command.

## Procedure

### Import the WebSphere Application Server Network Deployment cell by using the WAS-ND-Cell list view page

  1. Open the WebSphere Application Server Network Deployment cell page and launch create dialog.

     ![](https://github.com/IBM/appnav/blob/master/images/importcell.1.png)

  1. Enter details and create the cell.
     1. Under the General details tab, enter a name for the cell.
     1. Click Endpoints and enter your host and port details.
     1. Click Credentials and enter a Kubernetes secret name, user name, and password to log in to your cell.
     1. Click the Create button to create your credentials secret.

        AttentionYou can create a new Kubernetes secret or choose an existing one. For a new one, the user name and 
        password you specify is stored as base 64 encoded values in the secret.

  1. Optional: Inspect the cell.
     1. Click cell name to see the detail view.
     1. Use the detail view to see cell details.


### Import the WebSphere Application Server Network Deployment by using the Kubernetes command-line tool

1.	Create the WebSphere Application Server Network Deployment cell resource.
    1. All fields that are shown are required.
    1. Credentials are a Kubernetes secret in the same namespace.
    1. Interval is the controller polling interval for syncing cells with Kubernetes resources.
    1. Create the WebSphere Application Server Network Deployment cell.yaml file.

    1. Create the resource with the command:
    
1. Create the secret for the cell credentials.
   1. The user name and password fields must be base 64 encoded.
   1. The secret must be in the same namespace as the corresponding cell.
   1. Create the secret.yaml file.

   1. Create the resource with the following command:
   
1.	Inspect twas-apps resources.

    Use the following commands to see your cell and its secret in the yaml format:

## Results

You get a WAS-ND-Cell Kubernetes resource that represents your WebSphere Application Server Network Deployment cell and 
one WAS-Traditional-App Kubernetes resource for each enterprise application deployed to that cell.

