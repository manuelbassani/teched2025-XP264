BTP XP264 master landscape
=============

All the internal info is aggregated in the following issue:  
  * https://github.tools.sap/kyma/backlog/issues/7596


TODO: Add the picture of the master btp landscape...  


<img width="1669" height="841" alt="image" src="https://github.com/user-attachments/assets/5e9093ca-051a-462e-9b93-c2b8132c7166" />


## Provider subaccount with shared services


  * allow_access

```
20.39.212.71/32,20.117.177.87/32,172.187.240.229/32,45.148.14.0/24,95.214.184.0/24,13.105.117.0/24,13.105.49.0/24,34.141.69.247,34.159.216.62,34.159.191.69,130.214.104.0/24,20.42.117.61/32,20.84.67.105/32,51.8.106.72/32,130.33.112.244/32,74.176.216.39/32,20.89.73.170/32
```

  * instance mapping

  * reconfigure hana cloud with another runtime context, for instance: uk-xp264  

In the aftermath, both the allow_access list nad the mappings will be updated

```
20.39.212.71/32,20.117.177.87/32,172.187.240.229/32,45.148.14.0/24,95.214.184.0/24,13.105.117.0/24,13.105.49.0/24,34.141.69.247,34.159.216.62,34.159.191.69,130.214.104.0/24,20.42.117.61/32,20.84.67.105/32,51.8.106.72/32,130.33.112.244/32,74.176.216.39/32,20.89.73.170/32,172.187.193.188/32,20.117.121.230/32,20.117.240.186/32
```

## s4hana HE4 destinations definitions  

  * http://s4hana.tdc.sap.com:50080/sap/opu/odata/sap/api_business_partner/?sap-client=400

<img width="1216" height="1028" alt="image" src="https://github.com/user-attachments/assets/b442c666-8bb5-4ad5-a193-7eb98c1daafa" />

### Rehearse the destination definition  

In order to be able to rehearse subaccount level destinations without writing any code all we need is managed SAP Approuter in the context of the subacount.  

The managed SAP Approuter is brought into the context of a subaccount with the SAP Workzone (Launchpad) service plans free or standard.  

SAP Workzone subacription requires the OIDC subaccount trust be established.  This means, you will need a user with the OIDC provider the subaccount has been trusted with.


  * https://btp-bootstrap-quovadis-fe2eef75.launchpad.cfapps.eu10.hana.ondemand.com/dynamic_dest/destination-service/destinations/QUOVADIS_HE4  
<img width="1195" height="455" alt="image" src="https://github.com/user-attachments/assets/641e42b8-887f-4235-81e3-695ce80413f8" />


```
{
  "owner": {
    "SubaccountId": "6a7fc37b-a1c4-49f7-989a-92c496bd891a",
    "InstanceId": null
  },
  "destinationConfiguration": {
    "KeyStorePassword": "Password1",
    "tokenServiceURLType": "Dedicated",
    "audience": "HE4_400_GCP",
    "Description": "QUOVADIS_HE4-api_business_partner",
    "authnContextClassRef": "urn:oasis:names:tc:SAML:2.0:ac:classes:PreviousSession",
    "tokenServiceUser": "QUOVADIS",
    "tokenServiceURL": "http://s4hana.tdc.sap.com:50081/sap/bc/sec/oauth2/token?sap-client=400",
    "sap-client": "400",
    "URL": "http://s4hana.tdc.sap.com:50081/sap/opu/odata/sap/api_business_partner",
    "Name": "QUOVADIS_HE4",
    "tokenServicePassword": "<QUOVADIS client password>",
    "assertionRecipient": "https://s4hana.tdc.sap.com:50081/sap/bc/sec/oauth2/token?sap-client=400",
    "Type": "HTTP",
    "HTML5.DynamicDestination": "true",
    "KeyStoreLocation": "quovadis_ateam-isveng.p12",
    "clientKey": "QUOVADIS",
    "Authentication": "OAuth2SAMLBearerAssertion",
    "nameIdFormat": "urn:oasis:names:tc:SAML:1.1:nameid-format:unspecified",
    "CloudConnectorLocationId": "he4",
    "SystemUser": "XP264",
    "ProxyType": "OnPremise"
  },
  "certificates": [
    {
      "Content": "MIIQeAIBAzCCEDIGCSqGSIb3DQEHAaCCECMEghAfMIIQGzCCCggGCSqGSIb3DQEHAaCCCfkEggn1MIIJ8TCCCe0GCyqGSIb3DQEMCgECoIIJeHcO5xW0ai3ZkwPTAhMAkGBSsOAwIaBQAEFMyS26dKft/dWRSIVg/SQvDnQmaSBBQTST14Lse+rKA3igKg4Q7gzIB0mAICBAA=",
      "Name": "quovadis_ateam-isveng.p12",
      "Type": "CERTIFICATE"
    }
  ],
  "authTokens": [
    {
      "type": "Bearer",
      "value": "GwmDlnqcH9CggrRYHJfc3I9TZgQ76rrgi2EdPYq-5OUyP3Vr",
      "http_header": {
        "key": "Authorization",
        "value": "Bearer GwmDlnqcH9CggrRYHJfc3I9TZgQ76rrgi2EdPYq-5OUyP3Vr"
      },
      "expires_in": "3600",
      "scope": "/IWFND/SG_MED_CATALOG_0001 /IWFND/SG_MED_CATALOG_0002 PYC_CFG_SRV_0001 PYC_CONF_SRV_0001 SAP_BW_INA_GETSERVERINFO_HTTP SAP_BW_INA_SRV_0001 ZAPI_BUSINESS_PARTNER_0001 ZAPI_SALES_ORDER_SRV_0001 ZMD_BUSINESSPARTNER_SRV_0001",
      "refresh_token": "GwmDlnqcH9CggrRYHJf83CREbIGGtARzGgkqNOuVc9n29LIV"
    }
  ]
}
```

### Run the destination against the target on premise system

  * https://btp-bootstrap-quovadis-fe2eef75.launchpad.cfapps.eu10.hana.ondemand.com/dynamic_dest/QUOVADIS_HE4/  
  * https://btp-bootstrap-quovadis-fe2eef75.launchpad.cfapps.eu10.hana.ondemand.com/dynamic_dest/QUOVADIS_HE4/?$format=json

  ```
  {
  "d": {
    "EntitySets": [
      "A_AddressEmailAddress",
      "A_AddressFaxNumber",
      "A_AddressHomePageURL",
      "A_AddressPhoneNumber",
      "A_BPAddrDepdntIntlLocNumber",
      "A_BPContactToAddress",
      "A_BPContactToFuncAndDept",
      "A_BPCreditWorthiness",
      "A_BPDataController",
      "A_BPEmployment",
      "A_BPFinancialServicesExtn",
      "A_BPFinancialServicesReporting",
      "A_BPFiscalYearInformation",
      "A_BPIntlAddressVersion",
      "A_BPRelationship",
      "A_BPTaxCompliance",
      "A_BuPaAddressUsage",
      "A_BuPaIdentification",
      "A_BuPaIndustry",
      "A_BusinessPartner",
      "A_BusinessPartnerAddress",
      "A_BusinessPartnerAlias",
      "A_BusinessPartnerBank",
      "A_BusinessPartnerContact",
      "A_BusinessPartnerIsBank",
      "A_BusinessPartnerPaymentCard",
      "A_BusinessPartnerRating",
      "A_BusinessPartnerRole",
      "A_BusinessPartnerTaxNumber",
      "A_BusPartAddrDepdntTaxNmbr",
      "A_CustAddrDepdntExtIdentifier",
      "A_CustAddrDepdntInformation",
      "A_Customer",
      "A_CustomerCompany",
      "A_CustomerCompanyText",
      "A_CustomerDunning",
      "A_CustomerSalesArea",
      "A_CustomerSalesAreaTax",
      "A_CustomerSalesAreaText",
      "A_CustomerTaxGrouping",
      "A_CustomerText",
      "A_CustomerUnloadingPoint",
      "A_CustomerWithHoldingTax",
      "A_CustSalesPartnerFunc",
      "A_CustSlsAreaAddrDepdntInfo",
      "A_CustSlsAreaAddrDepdntTaxInfo",
      "A_CustUnldgPtAddrDepdntInfo",
      "A_Supplier",
      "A_SupplierCompany",
      "A_SupplierCompanyText",
      "A_SupplierDunning",
      "A_SupplierPartnerFunc",
      "A_SupplierPurchasingOrg",
      "A_SupplierPurchasingOrgText",
      "A_SupplierText",
      "A_SupplierWithHoldingTax"
    ]
  }
}
  ```


## Next steps  


### Prepare nodejs function code to run this destination via CloudSDK from kyma cluster side  


## jupyter hub

```
$ pip install matplotlib
Defaulting to user installation because normal site-packages is not writeable
Collecting matplotlib
  Downloading matplotlib-3.10.7-cp312-cp312-manylinux2014_x86_64.manylinux_2_17_x86_64.whl.metadata (11 kB)
Collecting contourpy>=1.0.1 (from matplotlib)
  Downloading contourpy-1.3.3-cp312-cp312-manylinux_2_27_x86_64.manylinux_2_28_x86_64.whl.metadata (5.5 kB)
Collecting cycler>=0.10 (from matplotlib)
  Downloading cycler-0.12.1-py3-none-any.whl.metadata (3.8 kB)
Collecting fonttools>=4.22.0 (from matplotlib)
  Downloading fonttools-4.60.1-cp312-cp312-manylinux1_x86_64.manylinux2014_x86_64.manylinux_2_17_x86_64.manylinux_2_5_x86_64.whl.metadata (112 kB)
Collecting kiwisolver>=1.3.1 (from matplotlib)
  Downloading kiwisolver-1.4.9-cp312-cp312-manylinux2014_x86_64.manylinux_2_17_x86_64.whl.metadata (6.3 kB)
Collecting numpy>=1.23 (from matplotlib)
  Downloading numpy-2.3.4-cp312-cp312-manylinux_2_27_x86_64.manylinux_2_28_x86_64.whl.metadata (62 kB)
Requirement already satisfied: packaging>=20.0 in /usr/local/lib/python3.12/site-packages (from matplotlib) (25.0)
Collecting pillow>=8 (from matplotlib)
  Downloading pillow-12.0.0-cp312-cp312-manylinux_2_27_x86_64.manylinux_2_28_x86_64.whl.metadata (8.8 kB)
Collecting pyparsing>=3 (from matplotlib)
  Downloading pyparsing-3.2.5-py3-none-any.whl.metadata (5.0 kB)
Requirement already satisfied: python-dateutil>=2.7 in /usr/local/lib/python3.12/site-packages (from matplotlib) (2.9.0.post0)
Requirement already satisfied: six>=1.5 in /usr/local/lib/python3.12/site-packages (from python-dateutil>=2.7->matplotlib) (1.17.0)
Downloading matplotlib-3.10.7-cp312-cp312-manylinux2014_x86_64.manylinux_2_17_x86_64.whl (8.7 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 8.7/8.7 MB 27.8 MB/s eta 0:00:00
Downloading contourpy-1.3.3-cp312-cp312-manylinux_2_27_x86_64.manylinux_2_28_x86_64.whl (362 kB)
Downloading cycler-0.12.1-py3-none-any.whl (8.3 kB)
Downloading fonttools-4.60.1-cp312-cp312-manylinux1_x86_64.manylinux2014_x86_64.manylinux_2_17_x86_64.manylinux_2_5_x86_64.whl (4.9 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 4.9/4.9 MB 25.7 MB/s eta 0:00:00
Downloading kiwisolver-1.4.9-cp312-cp312-manylinux2014_x86_64.manylinux_2_17_x86_64.whl (1.5 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 1.5/1.5 MB 15.0 MB/s eta 0:00:00
Downloading numpy-2.3.4-cp312-cp312-manylinux_2_27_x86_64.manylinux_2_28_x86_64.whl (16.6 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 16.6/16.6 MB 23.8 MB/s eta 0:00:00
Downloading pillow-12.0.0-cp312-cp312-manylinux_2_27_x86_64.manylinux_2_28_x86_64.whl (7.0 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 7.0/7.0 MB 23.4 MB/s eta 0:00:00
Downloading pyparsing-3.2.5-py3-none-any.whl (113 kB)
Installing collected packages: pyparsing, pillow, numpy, kiwisolver, fonttools, cycler, contourpy, matplotlib
  WARNING: The scripts f2py and numpy-config are installed in '/home/jovyan/.local/bin' which is not on PATH.
  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
  WARNING: The scripts fonttools, pyftmerge, pyftsubset and ttx are installed in '/home/jovyan/.local/bin' which is not on PATH.
  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
Successfully installed contourpy-1.3.3 cycler-0.12.1 fonttools-4.60.1 kiwisolver-1.4.9 matplotlib-3.10.7 numpy-2.3.4 pillow-12.0.0 pyparsing-3.2.5

[notice] A new release of pip is available: 25.0.1 -> 25.2
[notice] To update, run: pip install --upgrade pip


$ pip install scipy
Defaulting to user installation because normal site-packages is not writeable
Collecting scipy
  Downloading scipy-1.16.2-cp312-cp312-manylinux2014_x86_64.manylinux_2_17_x86_64.whl.metadata (62 kB)
Requirement already satisfied: numpy<2.6,>=1.25.2 in ./.local/lib/python3.12/site-packages (from scipy) (2.3.4)
Downloading scipy-1.16.2-cp312-cp312-manylinux2014_x86_64.manylinux_2_17_x86_64.whl (35.7 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 35.7/35.7 MB 23.8 MB/s eta 0:00:00
Installing collected packages: scipy
Successfully installed scipy-1.16.2

[notice] A new release of pip is available: 25.0.1 -> 25.2
[notice] To update, run: pip install --upgrade pip
$ 


$ pip install ipywidgets
Defaulting to user installation because normal site-packages is not writeable
Collecting ipywidgets
  Downloading ipywidgets-8.1.7-py3-none-any.whl.metadata (2.4 kB)
Requirement already satisfied: comm>=0.1.3 in /usr/local/lib/python3.12/site-packages (from ipywidgets) (0.2.3)
Requirement already satisfied: ipython>=6.1.0 in /usr/local/lib/python3.12/site-packages (from ipywidgets) (9.6.0)
Requirement already satisfied: traitlets>=4.3.1 in /usr/local/lib/python3.12/site-packages (from ipywidgets) (5.14.3)
Collecting widgetsnbextension~=4.0.14 (from ipywidgets)
  Downloading widgetsnbextension-4.0.14-py3-none-any.whl.metadata (1.6 kB)
Collecting jupyterlab_widgets~=3.0.15 (from ipywidgets)
  Downloading jupyterlab_widgets-3.0.15-py3-none-any.whl.metadata (20 kB)
Requirement already satisfied: decorator in /usr/local/lib/python3.12/site-packages (from ipython>=6.1.0->ipywidgets) (5.2.1)
Requirement already satisfied: ipython-pygments-lexers in /usr/local/lib/python3.12/site-packages (from ipython>=6.1.0->ipywidgets) (1.1.1)
Requirement already satisfied: jedi>=0.16 in /usr/local/lib/python3.12/site-packages (from ipython>=6.1.0->ipywidgets) (0.19.2)
Requirement already satisfied: matplotlib-inline in /usr/local/lib/python3.12/site-packages (from ipython>=6.1.0->ipywidgets) (0.1.7)
Requirement already satisfied: pexpect>4.3 in /usr/local/lib/python3.12/site-packages (from ipython>=6.1.0->ipywidgets) (4.9.0)
Requirement already satisfied: prompt_toolkit<3.1.0,>=3.0.41 in /usr/local/lib/python3.12/site-packages (from ipython>=6.1.0->ipywidgets) (3.0.52)
Requirement already satisfied: pygments>=2.4.0 in /usr/local/lib/python3.12/site-packages (from ipython>=6.1.0->ipywidgets) (2.19.2)
Requirement already satisfied: stack_data in /usr/local/lib/python3.12/site-packages (from ipython>=6.1.0->ipywidgets) (0.6.3)
Requirement already satisfied: parso<0.9.0,>=0.8.4 in /usr/local/lib/python3.12/site-packages (from jedi>=0.16->ipython>=6.1.0->ipywidgets) (0.8.5)
Requirement already satisfied: ptyprocess>=0.5 in /usr/local/lib/python3.12/site-packages (from pexpect>4.3->ipython>=6.1.0->ipywidgets) (0.7.0)
Requirement already satisfied: wcwidth in /usr/local/lib/python3.12/site-packages (from prompt_toolkit<3.1.0,>=3.0.41->ipython>=6.1.0->ipywidgets) (0.2.14)
Requirement already satisfied: executing>=1.2.0 in /usr/local/lib/python3.12/site-packages (from stack_data->ipython>=6.1.0->ipywidgets) (2.2.1)
Requirement already satisfied: asttokens>=2.1.0 in /usr/local/lib/python3.12/site-packages (from stack_data->ipython>=6.1.0->ipywidgets) (3.0.0)
Requirement already satisfied: pure-eval in /usr/local/lib/python3.12/site-packages (from stack_data->ipython>=6.1.0->ipywidgets) (0.2.3)
Downloading ipywidgets-8.1.7-py3-none-any.whl (139 kB)
Downloading jupyterlab_widgets-3.0.15-py3-none-any.whl (216 kB)
Downloading widgetsnbextension-4.0.14-py3-none-any.whl (2.2 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 2.2/2.2 MB 48.2 MB/s eta 0:00:00
Installing collected packages: widgetsnbextension, jupyterlab_widgets, ipywidgets
Successfully installed ipywidgets-8.1.7 jupyterlab_widgets-3.0.15 widgetsnbextension-4.0.14

[notice] A new release of pip is available: 25.0.1 -> 25.2
[notice] To update, run: pip install --upgrade pip


$ pip install beautifulsoup4
Defaulting to user installation because normal site-packages is not writeable
Requirement already satisfied: beautifulsoup4 in /usr/local/lib/python3.12/site-packages (4.13.3)
Requirement already satisfied: soupsieve>1.2 in /usr/local/lib/python3.12/site-packages (from beautifulsoup4) (2.6)
Requirement already satisfied: typing-extensions>=4.0.0 in /usr/local/lib/python3.12/site-packages (from beautifulsoup4) (4.13.2)

[notice] A new release of pip is available: 25.0.1 -> 25.2
[notice] To update, run: pip install --upgrade pip
  
```

