# Inventory Action

The Application Navigator inventory action provides an easy way to generate a report listing: 

1. All Application Navigator Kubernetes resources
1. All Application Navigator Pods and Images 
1. All Applications and components 
1. All WAS-ND-Cell and WAS-Traditional-App resources
1. All Liberty-Collective and Liberty-App resources 

This report provides an easy way to obtain an overall view of Application Navigator, it's operational status, and the resources
it is managing. 

To submit the Inventory actionn, simply click the "Inventory" in the Command Action table or "Run Inventory" button: 

![inventory](https://github.com/IBM/appnav/blob/master/docs/images/inventory.png)

Figure 1. Launch inventory action from Command Actions page 

There are two ways to launch the inventory action: 

1. The first time you open the "Command Actions" page

   There is a single entry in the table that states: 

   "No actions have been submitted yet. Want to run the __Inventory__ action?"  

   If you click on the highlighted word, "Inventory", the inventory action will be submitted. 

2. Any time you open the "Command Actions" page

   Just click the "Run Inventory" button, located in the upper right hand portion of the page, to submit the inventory action.
   

Example of Inventory action output: 

```
Begin IBM Application Navigator inventory ...

Tue May 26 18:40:46 UTC 2020

Starting server defaultServer.
Server defaultServer started with process ID 28.
App Navigator resources in kappnav namespace:

NAME                                                     READY   STATUS    RESTARTS   AGE
pod/kappnav-a005b257-82d2-4ab2-9636-f0ba24d7075f-k6lt8   1/1     Running   0          56s
pod/kappnav-controller-5d6f6685d7-xthkt                  2/2     Running   0          12d
pod/kappnav-operator-6cd5b7555c-kkrwt                    1/1     Running   0          12d
pod/kappnav-ui-6688ccd4d5-6kkwf                          3/3     Running   0          12d
pod/kappnav-was-controller-79c5ddb6b5-ndjtw              1/1     Running   0          12d

NAME                               TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)             AGE
service/kappnav-operator-metrics   ClusterIP   172.30.200.68    <none>        8383/TCP,8686/TCP   19d
service/kappnav-ui-service         ClusterIP   172.30.192.223   <none>        443/TCP             19d

NAME                                     READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/kappnav-controller       1/1     1            1           19d
deployment.apps/kappnav-operator         1/1     1            1           19d
deployment.apps/kappnav-ui               1/1     1            1           19d
deployment.apps/kappnav-was-controller   1/1     1            1           19d

NAME                                                DESIRED   CURRENT   READY   AGE
replicaset.apps/kappnav-controller-5d6f6685d7       1         1         1       19d
replicaset.apps/kappnav-operator-6cd5b7555c         1         1         1       19d
replicaset.apps/kappnav-ui-6688ccd4d5               1         1         1       19d
replicaset.apps/kappnav-was-controller-79c5ddb6b5   1         1         1       19d

NAME                                                     COMPLETIONS   DURATION   AGE
job.batch/kappnav-a005b257-82d2-4ab2-9636-f0ba24d7075f   0/1           56s        56s

NAME                                          HOST/PORT                                                PATH   SERVICES             PORT    TERMINATION   WILDCARD
route.route.openshift.io/kappnav-ui-service   kappnav-ui-service-kappnav.apps.lemurs.os.fyre.ibm.com          kappnav-ui-service   <all>   reencrypt     None

App Navigator Pods and Images:

pod=kappnav-a005b257-82d2-4ab2-9636-f0ba24d7075f-k6lt8
   docker.io/kappnav-test/app-nav-inv:latest

pod=kappnav-controller-5d6f6685d7-xthkt
   docker.io/kappnav-test/app-nav-apis:latest
   docker.io/kappnav-test/app-nav-controller:latest

pod=kappnav-operator-6cd5b7555c-kkrwt
   docker.io/kappnav-test/app-nav-operator

pod=kappnav-ui-6688ccd4d5-6kkwf
   docker.io/kappnav-test/app-nav-apis:latest
   docker.io/kappnav-test/app-nav-ui:latest
   quay.io/openshift/origin-oauth-proxy:4.3.0

pod=kappnav-was-controller-79c5ddb6b5-ndjtw
   docker.io/kappnav-test/app-nav-was-controller:latest

Searching for applications

Received application data from API server
Application my-project, namespace appsody
   Components:
     kind=Deployment, name=my-project, namespace=appsody
     kind=Service, name=my-project, namespace=appsody
     kind=Route, name=my-project, namespace=appsody
Application bookinfo, namespace bookinfo
   Components:
     kind=Application, name=details-app, namespace=bookinfo
     kind=Application, name=productpage-app, namespace=bookinfo
     kind=Application, name=ratings-app, namespace=bookinfo
     kind=Application, name=reviews-app, namespace=bookinfo
Application details-app, namespace bookinfo
   Components:
     kind=Service, name=details, namespace=bookinfo
     kind=Deployment, name=details-v1, namespace=bookinfo
Application productpage-app, namespace bookinfo
   Components:
     kind=Service, name=productpage, namespace=bookinfo
Application ratings-app, namespace bookinfo
   Components:
     kind=Service, name=ratings, namespace=bookinfo
     kind=Deployment, name=ratings-v1, namespace=bookinfo
Application reviews-app, namespace bookinfo
   Components:
     kind=Service, name=reviews, namespace=bookinfo
Application demo-app, namespace liberty
   Components:
     kind=Deployment, name=demo-app, namespace=liberty
     kind=Service, name=demo-app, namespace=liberty
     kind=Route, name=demo-app, namespace=liberty
Application stock-trader, namespace stock-trader
   Components:
     kind=Deployment, name=loyalty-level, namespace=stock-trader
     kind=Deployment, name=notification-twitter, namespace=stock-trader
     kind=Deployment, name=portfolio, namespace=stock-trader
     kind=Deployment, name=stock-quote, namespace=stock-trader
     kind=Deployment, name=trader, namespace=stock-trader
     kind=Service, name=loyalty-level-service, namespace=stock-trader
     kind=Service, name=notification-service, namespace=stock-trader
     kind=Service, name=portfolio-service, namespace=stock-trader
     kind=Service, name=stock-quote-service, namespace=stock-trader
     kind=Service, name=trader-service, namespace=stock-trader

Searching for tWAS Cells

WAS ND Cell kappnav-test-cell1, namespace twas
   tWAS Apps:
      defaultapplication.kappnav-test-cell1
      ivt.application.kappnav-test-cell1
WAS ND Cell wascell1, namespace wasnd
   tWAS Apps:
      ivt.application.wascell1
      query.wascell1
      websphereoidcrpdmgr.wascell1

Searching for Liberty-Collectives

Liberty Collective kappnav-test-collective1, namespace liberty
   Liberty Apps:
      appresortswar.kappnav-test-collective1
      messaging.kappnav-test-collective1
      snoop.kappnav-test-collective1
Liberty Collective coll1, namespace wasnd
   Liberty Apps:
      appresortswar.coll1
      messaging.coll1
      snoop.coll1


Stopping server defaultServer.
Server defaultServer stopped.
Tue May 26 18:41:46 UTC 2020
... IBM Application Navigator inventory done.


```

