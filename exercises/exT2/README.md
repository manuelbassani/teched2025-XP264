# Exercise T2 - Configure Transparent Proxy Kyma Module

In this exercise, you will configure Transparent Proxy as module in Kyma. This will allow you to locally consume destinations that managed centrally in SAP BTP Destination service, from within the Kyma instanc in a unified and virtually transparent way.

## Exercise T2.1 Navigate to your working Namespace in Kyma Dashboard

In the home page of Kyma Dashboard, navigate to your working Namespace.

1. Navigate to the Namespaces Overview
<br>![](/exercises/exT2/images/T2_01_01.png)

2. Select your working Namespace:
<br>![](/exercises/exT2/images/T2_01_02.png)

3. You see an overview of your Namespace
<br>![](/exercises/exT2/images/T2_01_03.png)

## Exercise T2.2 Create a _dynamic_ Destination Custom Resource

In the home page of the Namespace of your choice, you can see Connectivity section, and under it you find Destination CR. Latter are used to formally expose and reference the destinations - either statically via dedicated or _static_ CRs or dynamically via _dynamic_ (gateway) CR.

1. Click here to create a new dynamic Destination CR
<br>![](/exercises/exT2/images/T2_02_01.png)

2. The actual Destination CR creation. In this example, the Destination CR is a _dynamic_ one used to reference any destination that is accessible in the context of the account in use by Transparent Proxy based on the applied configuration.
<br>![](/exercises/exT2/images/T2_02_02.png)

3. Overview of the available Destination CRs
<br>![](/exercises/exT2/images/T2_02_03.png)
<br>![](/exercises/exT2/images/T2_02_04.png)

## Exercise T2.3 Create a _static_ Destination Custom Resource

In the home page of the Namespace of your choice, you can see Connectivity section, and under it you find Destination CR. Latter are used to formally expose and reference the destinations - either statically via dedicated or _static_ CRs or dynamically via _dynamic (gateway) CR.

1. Click here to create a new Destination CR
<br>![](/exercises/exT2/images/T2_03_01.png)

2. The actual Destination CR creation. In this example, the Destination CR is a _static_ one used to reference a specific destination that is accessible in the context of the account in use by Transparent Proxy based on the applied configuration.
<br>![](/exercises/exT2/images/T2_03_02.png)

3. Overview of the available Destination CRs
<br>![](/exercises/exT2/images/T2_03_03.png)
<br>![](/exercises/exT2/images/T2_03_04.png)

## Exercise T2.4 Explore the results of the creation of the Destination CRs via Kubectl

1. Explore Destination CRs via Terminal and Kubectl Command Line Tool
```
kubectl get destinations -n quovadis-btp
NAME      AGE     DESTINATIONREF   FRAGMENTREF   DESTINATIONSERVICEINSTANCENAME   SERVICEPORT   ACCESSCONTROLSCOPE   STATUS                    CHAINREF
gateway   4d4h    *                                                                                                  ConfigurationSuccessful   
s4any     6m39s   s4-anywhere                                                                                        ConfigurationSuccessful   
```
2. Explore available Kubernetes Services via Terminal and Kubectl Command Line Tool
```
kubectl get services -n quovadis-btp
NAME      TYPE           CLUSTER-IP   EXTERNAL-IP                                               PORT(S)   AGE
gateway   ExternalName   <none>       gateway-x4rf8.sap-transp-proxy-system.svc.cluster.local   <none>    4d4h
s4any     ExternalName   <none>       s4any-5cmhg.sap-transp-proxy-system.svc.cluster.local     <none>    7m11s
```

## Summary

You've now <b>configured</b> the Transparent Proxy via dynamic (gateway) Destination CR, and <b>enabled</b> local workloads to technically connect to any remote system defined as a destination in Destination service in the context of the account in use by Transparent Proxy based on the applied configuration.

Continue to - [Exercise T3 - Use Transparent Proxy Kyma Module ](../exT3/README.md)
