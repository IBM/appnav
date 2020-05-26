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

![]()

Figure 1. Logging section of kappnav resource

