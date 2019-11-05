# Adding a WebSphere Application Server Network Deployment application or Liberty application to a cloud application

IBM Application Navigator enables you to import WebSphere® Application Server Network Deployment cells that automatically include WebSphere enterprise applications, and twas-apps Kubernetes resources, into your Kubernetes cluster. You can then add these enterprise applications as components to cloud applications that can be viewed with Application Navigator.

## About this task

You can make a twas-app Kubernetes resource a component of a Kubernetes application resource by importing cells into your Kubernetes cluster. A representation of the twas-apps resource in the cell is created during the import instead of an import of the actual twas-apps resource.

## Procedure

1. Choose the applications to which you want to add the twas-app resource.

    Find all applications by using the command:
    ```
    kubectl get applications --all-namespaces
    ```
2. Determine the labeling scheme that the application uses.
    
    List the application's label selector by using the command:
    ```
    kubectl get application <application-name> -n <application-namespace> -o yaml
    ```

The target application can specify either a match label, with an autonomous membership, or a match expression, with a directed membership, for its label selector. For more information, see [Cloud native applications on Kubernetes with Application Navigator](https://www.ibm.com/support/knowledgecenter/SSAW57_9.0.5/com.ibm.websphere.nd.multiplatform.doc/ae/rcld_cloud_appnav.html).

3. Add the twas-app resource to the target application according to its labeling scheme.
    1. For autonomous membership, update the twas-app resource to have a matching label by using the following command syntax:
    ```
    kubectl label twas-app <twas-app-name>  -n <twas-app-namespace> <label>=<label-value>
    ```
    For example: 
    ```
    kubectl label twas-app query -n stock-trader solution=stock-traderCopy
    ```
    2. For directed membership, you must update the application resource. You can do this update from the Application Navigator main menu page or with the **Kubernetes** command-line tool.
     * Find the application on the Application Navigator main menu, then from the **Action** menu click **Edit** for the target application.

     ![](images/addtwaslib.1.png?raw=true)

     You can add the **app** label value of the twas-app resource to the application and save your change.

     ![](images/addtwaslib.2.png?raw=true)

     * With the **Kubernetes** command-line tool, you can update the original application definition and apply the change with the following command:
     
     ```
     kubectl apply -f application.yaml
     ```

     > **Important**: Application components must be in the same namespace as the application that they are a part of.
