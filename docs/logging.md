# Application Navigator Logging

Application Navigator supports a hierarchical
log level scheme, where each successive log level includes a lower log level. The data that is stored in logs helps to determine problems within applications.

Logging is supported for each of the Application Navigator container types. The following log levels are supported: 

|Log level|Description|
|---|----------|
| `none` | Turn off logging | 
| `error` | Record only `error` messages | 
| `warning` | Record only `warning` and `error` messages | 
| `info` | Record only `info`, `warning`, and `error` messages  |
| `debug` | Record only `debug`, `info`, `warning`, and `error` messages
| `entry` | Record only `entry` and `exit`, `debug`, `info`, `warning`, and error messages 
| `all` | Records all message types

The default log level is `info`.

## Setting log levels

Log levels are set by editing the kappnav instance through the OpenShift Administrator console. You can use the **Home > Explorer > kappnav > instances > kappnav > yaml** console path to find the kappnav instance that is used to edit log levels as shown in the following example: 

![Logging section of kappnav resource](https://github.com/IBM/appnav/blob/master/docs/images/loglevels.png)


Within the kappnav instance, you can change the logging level for any Application Navigator container. The following example shows the output after you change the log level: 

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

## Finding Application Navigator Logs 

Containers generate logs and are found in pods. The following example specifies the Application Navigator pods along with their corresponding containers:

|Pod|Containers|
|---|----------|
| `controller` | `controller`, `apis` | 
| `operator` | `operator` | 
| `ui` | `ui`, `apis` | 
| `was-controller` | `was-controller` |

If you modify the logging level for any container, the change affects all of the container instances, including each pod that the container exists in.

You can use the **Workloads > Pods > pod-name > logs > container-name** console path in the OpenShift Administrator console to access a container's log. The following example shows how to access an Application Navigator container log: 

![Application Navigator container log](https://github.com/IBM/appnav/blob/master/docs/images/logs.png)



