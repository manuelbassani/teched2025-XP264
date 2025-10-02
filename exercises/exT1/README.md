# Exercise T1 - Enable Transparent Proxy Kyma Module

In this exercise, you will enable Transparent Proxy as module in Kyma. This will allow you to further configure it and expose destinations managed centrally in SAP BTP Destination service for local,unified and virtually transparent consumption within the Kyma instance.

## Exercise T1.1 Navigate To The Kyma Dashboard

Once working with BTP cockpit and navigated to the account overview page, you can switch the working context to the Kyma Dashboard

1. Click here.
<br>![](/exercises/exT1/images/T1_01_01.png)

2. As result, you're navigated to the Kyma Dashbaord:
<br>![](/exercises/exT1/images/T1_01_02.png)



## Exercise T1.2 Enable Transparent Proxy Module 

In the home page of the Kyma Dashabord, you can see an overview of the Kyma instance, for example, health status, important metadata, and link to the modules.

<br>![](/exercises/exT1/images/T1_02_01.png)

1. Click here.
<br>![](/exercises/exT1/images/T1_02_02.png)

2. Module enablement has started. You may see it being in processing state
<br>![](/exercises/exT1/images/T1_02_03.png)

3. In a while, the module has been enabled and in healthy state, ready for further configuration and usage
<br>![](/exercises/exT1/images/T1_02_04.png)

## Exercise T1.2 Explore What Changed In The Kyma Instance

Once Transparent Proxy is enabled as Kyma Module, a new dedicated system namespace is created for it called _sap-transp-proxy-system_. Please beware that upon Transparent Proxy updates/upgrades or deletion, any changes done manually within this namespace will be lost or overriden by the module lifecycle automation responsible Operator.

Transparent Proxy Operator is using BTP Operator module to automatically "wire" or configure it with a service instance of Destination service. In addition, if Connectivity Proxy module has been previously enabled, it would be automatically "wired" as well. You can explore this in the module configuration.

If interested or simply out of curiosity, you may further expolore the _sap-transp-proxy-system_ namespace.

## Summary

You've now <b>enabled</b> Transparent Proxy as Kyma Module. It's lifecycle management is governed by a special module operator, ensuring the target and actual state of the module do not differ and the module is healthy and available for the side workloads runing in the Kyma instance.

Continue to - [Exercise T2 - Configure Transparent Proxy Kyma Module ](../exT2/README.md)
