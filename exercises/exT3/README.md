# Exercise T3 - Use Transparent Proxy Kyma Module

In this exercise, you will consume remote systems defined as destinations managed centrally in SAP BTP Destination service in a unified and virtually transparent way, powered by Transparent Proxy module, seamlessly integrated with other modules and services of SAP BTP Connectivity.

For simplicity and illustration purposeses, you'd be starting cURL Pod and use the well-known cURL tool to technially connect and perform requests to the target systems.

## Exercise T3.1 Run a cURL Pod Included in the Istio Service Mesh

Using a single command, you will run a Kubernetes Pod hosting a preconfigured environment allowing direct usage of cURL. To be able to access remote systems securely exposed via Transparent Proxy, the Kuberenetes Pod must be included in the Istio Service Mesh.

1. Execute the following command in the terminal

Command:
```
kubectl run -n quovadis-btp --labels=sidecar.istio.io/inject=true -it --rm --image=curlimages/curl-base curly -- /bin/sh
```
Output:
```
All commands and output from this session will be recorded in container logs, including credentials and sensitive information passed through the command prompt.
If you don't see a command prompt, try pressing enter.
/home/curl_user #

```

2. Install _jq_ for being able to easily parse the JSON response from the target system

Command:
```
apk add jq
```
Output:
```
fetch https://dl-cdn.alpinelinux.org/alpine/v3.22/main/x86_64/APKINDEX.tar.gz
fetch https://dl-cdn.alpinelinux.org/alpine/v3.22/community/x86_64/APKINDEX.tar.gz
(1/2) Installing oniguruma (6.9.10-r0)
(2/2) Installing jq (1.8.0-r0)
Executing busybox-1.37.0-r19.trigger
OK: 18 MiB in 39 packages
```

## Exercise T3.2 Connect to remote systems defined as destinations using the dynamic "gateway" Destination CR

This ```gateway``` Destination CR can be used to invoke any of the available destinations in the context of the BTP subaccount. For example, let's use the ```cis-httpbin``` destination which targets ```httpbin.org``` system hosted in Internet - a simple HTTP Request & Response Service.

1. Execute the following command in the terminal

Request Command:
```
curl gateway/headers -s -H "X-Destination-Name: cis-httpbin" | jq .headers.Host
```
Response:
```
"httpbin.org"
```

If you'd like to explore the raw JSON output, re-execute the commant ommiting the suffux ```| jq .headers.Host```.

## Exercise T3.3 Connect to a remote system defined as destination using the dedicated (static) "s4any" Destination CR

This ```s4any``` Destination CR points to ```s4-anywhere``` destination which targets an SAP S/4HANA system hosted in the premise and securely exposed to BTP applications via Cloud Connector and SAP Connectivity service. In this example, we will use the [Business Partner (A2X)
](https://api.sap.com/api/API_BUSINESS_PARTNER/overview) OData API and more specifically [GET /A_BusinessPartner](https://api.sap.com/api/API_BUSINESS_PARTNER/resource/get_A_BusinessPartner)

1. Execute the following command in the terminal
Request:
```
curl -s 's4any/sap/opu/odata/sap/api_business_partner/A_BusinessPartner?sap-client=400&$top=5&$select=BusinessPartnerFullName&$format=json' -H "Authorization: $(cat token)" | jq .d.results[].BusinessPartnerFullName
```
Response:
```
"US Apparel DC"
"US Grocery DC"
"Philadelphia Store"
"New York Store"
"Boston Store"
```

If you'd like to explore the raw JSON output, re-execute the commant ommiting the suffux ```| jq .d.results[].BusinessPartnerFullName```.

2. As you might already guess, the same request can technically be performed using the ```gateway``` Destination CR. Here's how it looks like:

Request:
```
curl -s 'gateway/sap/opu/odata/sap/api_business_partner/A_BusinessPartner?sap-client=400&$top=5&$select=BusinessPartnerFullName&$format=js
on' -H "X-Destination-Name: s4-anywhere" -H "Authorization: $(cat token)" | jq .d.results[].BusinessPartnerFullName
```
Response:
```
"US Apparel DC"
"US Grocery DC"
"Philadelphia Store"
"New York Store"
"Boston Store"
```

## Summary

You've now consumed remote systems defined as destinations in Destination service in the context of the account in use by Transparent Proxy based on the applied configuration.

You see how simple is to connect to arbirtary system defined as a destination in Destination service. You practically use the Destination CR as locally accessible hostname and do not do anything more but passing the mandatory API specific parameters. The complex parts are handled automatically by the Transparent Proxy and Destination service. If the target system is hosted on-premise, then the additional complexity is again handled automatically, this time with the automated usage of Connectivity Proxy module and Connectivity service.

Continue to - [Exercise N - Excercise N ](../exN/README.md)
