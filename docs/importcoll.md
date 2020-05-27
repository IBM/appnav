# Import Liberty Collectives

Importing a WebSphere&reg; Liberty collective creates a Liberty-Collective Kubernetes custom resource to represent the collective.
Application Navigator automatically discovers applications that are deployed on the collective and creates Liberty-App Kubernetes custom resources to represent those applications.
Application Navigator periodically polls the collective to keep the state of the Liberty-Collective resources and Liberty-App resources synchronized with the collective.

## About this task

You can import an existing WebSphere Liberty collective into IBM Application Navigator to establish
visibility and access to the collective. A collective can be imported
into Application Navigator with the 'Liberty Collectives' page in Application Navigator or the Kubernetes kubectl command.

## Procedure

### Import the WebSphere Liberty collective using the 'Liberty Collectives' page

  1. Open the WebSphere Liberty collective page and launch create dialog.

     ![](images/importcollective.1.png?raw=true)

  1. Enter details and create the collective.

     1. Under the **General** details tab, enter a name for the collective.

        ![](images/importcollective.2.png?raw=true)

     1. Click **Endpoints** and enter your host name, and adjust any port values (defaults are provided).

        ![](images/importcollective.3.png?raw=true)

     1. Click Credentials and enter a Kubernetes secret name, user name, and password to log in to your collective.

         ![](images/importcollective.4.png?raw=true)

     1. Click the **Create** button to create your credentials secret.

        **Attention:** You can create a new Kubernetes secret or choose an existing one. For a new one, the user name and
        password you specify is stored as base 64 encoded values in the secret.

  1. Optional: Inspect the collective.

     1. Click collective name to see the detail view.

        ![](images/importcollective.5.png?raw=true)

     1. Use the detail view to see collective details.

        ![](images/importcollective.6.png?raw=true)


### Import the WebSphere Liberty collective by using the Kubernetes command-line tool

1.	Create the WebSphere Liberty collective resource.
    1. All fields that are shown are required.
    1. Credentials are a Kubernetes secret in the same namespace.
    1. Interval is the controller polling interval for syncing collectives with Kubernetes resources.
    1. Create the `collective.yaml` file:

       ```
       apiVersion: kappnav.io/v1beta1
       kind: Liberty-Collective
       metadata:
          name: existing-collective
          namespace: default
       spec:
          console_url: https://existing-collective.example.com:9043/adminCenter
          credentials: existing-collective-secret
          interval: 30
       ```

    1. Create the resource with the command:

       ```
       kubectl create -f collective.yaml
       ```

1. Create the secret for the collective credentials.
   1. The user name and password fields must be base 64 encoded.
   1. The secret must be in the same namespace as the corresponding collective.
   1. Create the `secret.yaml` file.

      ```
      apiVersion: v1
      data:
         password: dGVzdHVzZXJwd2Q=
         username: dGVzdHVzZXI=
      kind: Secret
      metadata:
         name: existing-collective-secret
         namespace: default
      ```

   1. Create the resource with the following command:

      ```
      kubectl create -f secret.yaml
      ```

1.	Inspect twas-apps resources.

    Use the following commands to see your collective and its secret in the `yaml` format:

    ```
    kubectl get liberty-collective existing-collective -o yaml
    kubectl get liberty-apps -o yaml
    kubectl get secret existing-collective-secret -o yaml
    ```

## Results

You get a Liberty-Collective Kubernetes resource that represents your WebSphere Liberty collective and
one Liberty-App Kubernetes resource for each enterprise application deployed to that collective.


