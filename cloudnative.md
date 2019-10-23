# Understanding Cloud Native Applications on Kubernetes

IBM Application Navigator defines applications as a set of Kubernetes resources that work together to satisfy a particular 
set of business requirements. Cloud native applications Cloud native applications are composed of distributed components. 
In a cloud native architecture, each component follows the principles that are specified by 12factor.net. These principles 
specify the logical architecture of a cloud native application as shown in the following diagram:

![](https://github.com/IBM/appnav/blob/master/images/cloudnative.1.png)
 
In the diagram, you can see the architecture of a simple cloud native application that is composed of a user-facing component,
Web App W. This component calls the Micro Service 1 and Micro Service 2 components. Each component provides a discrete 
function. The following diagram shows the components as Application A. The components work together and satisfy an overall 
business need.

![](https://github.com/IBM/appnav/blob/master/images/cloudnative.2.png)
 
## Kubernetes applications

The logical architecture of a cloud native application can be implemented and deployed to various environments. In the 
following diagram, it is implemented in Java. The architecture uses [Open Liberty](https://openliberty.io/) and deploys to a Kubernetes-based
cloud platform, such as Red Hat Openshift. When the architecture is deployed to Kubernetes, the logical
components turn into various Kubernetes resources as the application is installed.

![](https://github.com/IBM/appnav/blob/master/images/cloudnative.3.png)
 
The diagram shows each component that is separately installed to Kubernetes. By following the 12 Factor principles, an owner 
can independently install and operate each component. Each owner can choose a different installation technology, such as Helm 
charts, Kubernetes operators, or even low-level Kubernetes configuration files. When an owner deploys components to Kubernetes, each component turns into one or more Kubernetes resources.
In the following diagram, you can see a Deployment and Pod resource for each component. These resources provide structure and
control over the software containers while the Service or Ingress resources provide network access. This set of components that are composed of resources defines the logical application boundary, for Application A. The logical application boundary uses an Application custom resource with Kubernetes.


![](https://github.com/IBM/appnav/blob/master/images/cloudnative.4.png)
 
## Application custom resource

The IBM Application Navigator uses the Kubernetes custom resource extension mechanism to define a custom resource kind, 
named Application, during its own installation. The Application kind is used to define a set of Kubernetes resources that 
make up your application. It uses a label selector to select resources that have a label that meets the specified criteria. 
The selected resources are the components of the application. IBM Application Navigator displays a list of applications, 
and a list of components for each application.

With the label selector for the Application kind, two principle patterns are commonly used:
- Autonomous membership
  - In autonomous membership, individual components choose to be part of a known application.
- Directed membership
  - In directed membership, the Application explicitly selects specific components.

### Autonomous Membership

In the autonomous membership pattern, the Application kind defines a label selector and any component that is part of that 
application specifies a matching label. In the following diagram, the Application specifies the label solution with a value 
of application-a. Any component in the same namespace that specifies that same label or value pair is selected as part of 
this application. The componentKinds attribute defines an array of kinds and only the specified kinds are selected as 
components of this application.


![](https://github.com/IBM/appnav/blob/master/images/cloudnative.5.png)
 
### Directed membership

In the directed membership pattern, the Application kind defines a label selector that specifies the specific components 
that are part of that application. In the following diagram, the Application kind specifies a label expression that selects
any component that has a label that is named app and a label value that matches any of the values in the specified list. The 
componentKinds attribute defines an array of kinds and only the specified kinds are selected as components of this 
application.

![](https://github.com/IBM/appnav/blob/master/images/cloudnative.6.png)
 
## Applications as components

Since applications themselves are Kubernetes resources, they can be specified as components of an application. In the 
following diagram, the application-c, constrains its component membership to be limited to only Application kind. When an 
application contains a component that is itself an application, the IBM Application Navigator enables multi-level navigation. 
This multi-level navigation allows you to drill into the top-level application, and then into its component list. For any 
component that is an application, you can then drill into it to see its component list.

![](https://github.com/IBM/appnav/blob/master/images/cloudnative.7.png)
