# IBM Application Navigator - Known Issues

Examine the list of known issues, by release, and potential corrective actions.

## V 4.1.0

### Problem: After adding a WAS ND Cell or Liberty Collective, the status remains "Unknown"
* Problem: After you add a WAS ND Cell or Liberty Collective, the status remains "Unknown" and no applications are discovered.
* Issue: An intermittent issue exists with the start-up order of the WAS Controller process, which runs as part of IBM Application Navigator. This process runs in a Kubernetes pod, which is created during the installation and managed as part of the Deployment. An unresolved issue can cause the WAS Controller process to fully process the creation of the WAS ND Cell and Liberty Collective resources, resulting in the "Unknown" status.
* Resolution: A work-around to the issue is to restart the WAS Controller, which triggers a reprocessing of the appropriate resources and establishes correct connections to the WAS ND cell or Liberty collective.
* Work-around Steps:
  1. Get a list of all the running pods with the `kubectl --namespace kappnav get pods` command.
     ```
     NAME                                      READY     STATUS      RESTARTS   AGE
     helm-operator-59bff68f9-ndn7f             1/1       Running     0          1d
     kappnav-controller-6cd7c45599-fvb9m       2/2       Running     0          1d
     kappnav-init-post-sdzpw                   0/1       Completed   0          1d
     kappnav-init-pre-s8jx5                    0/1       Completed   0          1d
     kappnav-ui-557cdddfb6-525fh               3/3       Running     0          1d
     kappnav-was-controller-5dd9fdc9f7-wwv4g   1/1       Running     0          1d
     ```
  1. Delete the kappnav-was-controller pod, for example, `kubectl --namespace kappnav delete pods kappnav-was-controller-5dd9fdc9f7-wwv4g`.
     ```
     # kubectl --namespace kappnav delete pods kappnav-was-controller-5dd9fdc9f7-wwv4g
     pod "kappnav-was-controller-5dd9fdc9f7-wwv4g" deleted
     ```
  1. The deployment restarts the process, creating a new pod.
