# Application Navigator Logging

All Application Navigator containers generate logs. The most common purpose for this data is to aid problem determination by
the IBM Support team. 

Logging is supported for each of the Application Navigator container types.  Application Navigator supports a hierarchial
log level scheme, where each successive log level includes lower log level.  The following log levels are supported: 

1. none - means turn off logging
1. error - means record only error messages 
1. warning - means record only warning and error messages 
1. info - means record only info, warning, and error messages 
1. debug - means record only debug, info, warning, and error messages
1. entry - means record only entry/exit, debug, info, warning, and error messages 
1. all - means records all message types 

**Note:** default log level is:  info

# How to set logging levels 

Log levels are set by editing the kappnav instance through the Openshift Administrator console.  Find the kappnav instance, 
using console path: 

**Home > Explorer > kappnav > instances > kappnav > yaml**

![loglevels](https://github.com/IBM/appnav/blob/master/docs/images/loglevels.png)

Figure 1. Logging section of kappnav resource

To change the logging level for any Application Navigator container or containers,  just edit the current log level to the desired log level and click the "save" button. 

**Sample Output**

```

Launching defaultServer (Open Liberty 19.0.0.12/wlp-1.0.35.cl191220191120-0300) on IBM J9 VM, version 8.0.5.41 - pxa6480sr5fp41-20190919_01(SR5 FP41) (en_US)
[AUDIT   ] CWWKE0001I: The server defaultServer has been launched.
[AUDIT   ] CWWKG0093A: Processing configuration drop-ins resource: /opt/ol/wlp/usr/servers/defaultServer/configDropins/defaults/keystore.xml
[AUDIT   ] CWWKG0093A: Processing configuration drop-ins resource: /opt/ol/wlp/usr/servers/defaultServer/configDropins/defaults/open-default-port.xml
[AUDIT   ] CWWKZ0058I: Monitoring dropins for applications.
[AUDIT   ] CWWKT0016I: Web application available (default_host): http://kappnav-controller-5d6f6685d7-khxtt:9080/openapi/ui/
[AUDIT   ] CWPKI0803A: SSL certificate created in 9.441 seconds. SSL key file: /opt/ol/wlp/output/defaultServer/resources/security/key.p12
[AUDIT   ] CWWKT0016I: Web application available (default_host): http://kappnav-controller-5d6f6685d7-khxtt:9080/openapi/
[AUDIT   ] CWWKF0012I: The server installed the following features: [appSecurity-2.0, beanValidation-1.1, cdi-1.2, distributedMap-1.0, el-3.0, jaxrs-2.0, jaxrsClient-2.0, jndi-1.0, json-1.0, mpConfig-1.2, mpOpenAPI-1.0, servlet-3.1, ssl-1.0, transportSecurity-1.0].
[AUDIT   ] CWWKF0011I: The defaultServer server is ready to run a smarter planet. The defaultServer server started in 62.469 seconds.
[AUDIT   ] CWWKZ0022W: Application kappnav has not started in 30.038 seconds.
[AUDIT   ] CWWKT0016I: Web application available (default_host): http://kappnav-controller-5d6f6685d7-khxtt:9080/kappnav/
[AUDIT   ] CWWKZ0001I: Application kappnav started in 35.857 seconds.
[WARNING ] CWWKW1002W: The CDI scope of JAXRS-2.0 Provider BeanValidationProvider is javax.enterprise.context.Dependent. Liberty gets the provider instance from CDI.
[err] SLF4J: Failed to load class "org.slf4j.impl.StaticLoggerBinder".
[err] SLF4J: Defaulting to no-operation (NOP) logger implementation
[err] SLF4J: See http://www.slf4j.org/codes.html#StaticLoggerBinder for further details.
[05/26/20 17:41:26:240 GMT] 143 com.ibm.kappnav.logging.Logger setLogLevel [INFO] Logging level is now INFO
[05/26/20 19:40:52:689 GMT] 155 com.ibm.kappnav.logging.Logger setLogLevel [INFO] Logging level is now DEBUG
```

# Finding Application Navigator Logs 

Containers generate logs.  Containers are found in pods.  Application Navigator has the following pods with the following containers. 

|Pod|Containers|
|---|----------|
| controller | controller, apis | 
| operator | operator | 
| ui | ui, apis | 
| was-controller | was-controller |

For example, if you modify the logging level for the "apis" container, it affects both container instances,  one in the controller pod, another in the ui pod. 

To access a container's log, use the Openshift Administrator console, using console path: 

**Workloads > Pods > pod-name > logs > container-name **

For example: 

![loglevels](https://github.com/IBM/appnav/blob/master/docs/images/logs.png)

Figure 2. Application Navigator container log

