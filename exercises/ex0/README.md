# Exercise 0 - Preparation Steps

You must have a personal github account for this session.  


## Exercise 0.0 - Sign up for a new GitHub account

This step is optional and you can be use instead any existing personal GitHub account of yours.

- Navigate to [GitHub](https://github.com/).
- Click **Sign up for GiHhub**.
- Otherwise, you may click on **Continue with Google** to sign up using your Google social login.
- Follow the prompts to create your personal account.

## Exercise 0.1 - Create a Copy of This Repository

 - Login to [GitHub](https://github.com/).
 - On the [main page of this repository](https://github.com/SAP-samples/teched2025-XP264), choose **Fork** on the top right.

<table style="width: 100%; border-collapse: collapse; background-color: #f5f5f5;" border="1">
<tbody>
<tr style="height: 193px;">
<td style="width: 71.6%; height: 193px;">
<div>
<h1><a href="https://github.com/SAP-samples/teched2025-XP264"><img class="aligncenter" src="../ex0/images/fork_entry.png" alt="" /></a></h1>
</div>
</td>
</tr>
</tbody>
</table>   

 - Make sure that the **Owner** matches the GitHub account that you want to use for this session. All the other information can remain the same.


<table style="width: 100%; border-collapse: collapse; background-color: #f5f5f5;" border="1">
<tbody>
<tr style="height: 193px;">
<td style="width: 71.6%; height: 193px;">
<div>
<h1><a href="https://github.com/SAP-samples/teched2025-XP264"><img class="aligncenter" src="../ex0/images/fork_details.png" alt="" /></a></h1>
</div>
</td>
</tr>
</tbody>
</table>   

 - Choose **Create Fork**. You are now brought to a copy of the repository in your GitHub account.
 - Choose **Activate Github Action**

## Exercise 0.2 - Discover SAP-TechEd25-XP264 Business Technology Platform landscape

- Login to [SAP-TechEd25-XP264 Business Technology Platform - Cockpit](https://emea.cockpit.btp.cloud.sap/cockpit?idp=anuk8cmfw.accounts.ondemand.com#/globalaccount/c1f19148-71f7-4883-9f86-8d5ee7634dec) with your allocated student's credentials (SSO)


<table style="width: 100%; border-collapse: collapse; background-color: #f5f5f5;" border="1">
<tbody>
<tr style="height: 193px;">
<td style="width: 71.6%; height: 193px;">
<div>
<h1><a href="https://emea.cockpit.btp.cloud.sap/cockpit?idp=anuk8cmfw.accounts.ondemand.com#/globalaccount/c1f19148-71f7-4883-9f86-8d5ee7634dec"><img class="aligncenter" src="../ex0/images/SAP-TechEd25-XP264.png" alt="SAP-TechEd25-XP264" /></a></h1>
</div>
</td>
</tr>
</tbody>
</table>   

- The BTP landscape has a number of subaccounts or runtime contexts.  
- Most of the runtime contexts are hosted in the same BTP region - in the EU20 data center (Azure/Netherlands)
- However, there are a few in the EU10 data center (AWS/Francfort) as well.
- Each BTP subaccount can host a single kyma runtime environment.
- Each kyma runtim environment maps into a single kuberneters cluster in the Azure or AWS region of your choice.
- Please note the kyma cluster region may be different from the BTP subaccount region.



### The rules of the game

- The students can pick and choose any available kyma cluster region from the following list:

| Account Name              | Type        |                                                                                                                                Description |
| :------------------------ | :---------: | :------------------------------------------------------------------------------------------------------------------------ |
| btp-runtime               |  US EAST region  | Students runtime context with kyma environment in the us east region         |
| uk-south                  |  UK SOUTH region | Students runtime contexts with kyma environment in the uk south region         |
| japan-east                |  JAPAN EAST region | Students runtime contexts with kyma environment in the japan east region         |




 | Region | Kubeconfig (download) | Console (dashboard) | Admin Worklow | Student Workflow | Data Collection Workflow
 | :--------- | :---------:  | --------- | :--------- | :------- | -----------
 | [uk-south](https://emea.cockpit.btp.cloud.sap/cockpit?idp=anuk8cmfw.accounts.ondemand.com#/globalaccount/c1f19148-71f7-4883-9f86-8d5ee7634dec/subaccount/4457fb7f-3296-40cf-b66b-aac3d9d4a2b2) | https://url.sap/q9176k | [<img src="../landscape/uksouth/kyma-dashboard_url_uksouth.png" width="100" />](https://dashboard.kyma.cloud.sap/?kubeconfigID=6D0AF763-179E-4F84-8ED0-724B3C0C2C92) | [uk-south--admin](../../../../actions/workflows/uk-south-teched-7a69075f-7faf-4604-a62e-806648791dba.yml) | [uk-south--xp264](../../../../actions/workflows/uk-south-teched-7a69075f-7faf-4604-a62e-806648791dba-xp264.yml)| [ k8s-data-context](../../../../actions/workflows/k8s-data-context-teched.yml)
 | [japan-east](https://emea.cockpit.btp.cloud.sap/cockpit?idp=anuk8cmfw.accounts.ondemand.com#/globalaccount/c1f19148-71f7-4883-9f86-8d5ee7634dec/subaccount/cae18034-657b-478d-89f7-b802b8111cd0) | https://url.sap/0nusi8 | [<img src="../landscape/japaneast/kyma_dashboard_url_japaneast.png" width="100" />](https://dashboard.kyma.cloud.sap/?kubeconfigID=79EB720B-2C16-4A7E-AA7F-108C4E3B7E98 ) | [japan-east--admin](../../../../actions/workflows/japan-east-teched-2a6fe480-ac84-4751-ad37-56ec2a493932.yml) | [japan-east--xp264](../../../../actions/workflows/japan-east-teched-2a6fe480-ac84-4751-ad37-56ec2a493932-xp264.yml) | [k8s-data-context](../../../../actions/workflows/k8s-data-context-teched.yml)
 | [us-east](https://emea.cockpit.btp.cloud.sap/cockpit?idp=anuk8cmfw.accounts.ondemand.com#/globalaccount/c1f19148-71f7-4883-9f86-8d5ee7634dec/subaccount/831741eb-0b10-4d2c-9feb-c49afec286f5) | https://url.sap/57qy47 | [<img src="../landscape/useast/kyma_dashboard_url_useast.png" width="100" />](https://dashboard.kyma.cloud.sap/?kubeconfigID=72A4A32B-0D0A-47DE-90C9-A65D52C8ADBE) | [us-east--admin](../../../../actions/workflows/btp-runtime-teched-dbe7346b-88da-430a-8777-4f6aa3e22b5e.yml) | [us-east--xp264](../../../../actions/workflows/btp-runtime-teched-dbe7346b-88da-430a-8777-4f6aa3e22b5e-xp264.yml) | [k8s-data-context](../../../../actions/workflows/k8s-data-context-teched.yml)
 | [xp264-000](https://emea.cockpit.btp.cloud.sap/cockpit?idp=anuk8cmfw.accounts.ondemand.com#/globalaccount/c1f19148-71f7-4883-9f86-8d5ee7634dec/subaccount/20b6061c-64aa-4397-bc01-df7348704173) | https://url.sap/jdleyl | [<img src="../landscape/xp264-000/kyma_dashboard_url_xp264_000.png" width="100" />](https://dashboard.kyma.cloud.sap/?kubeconfigID=B427F082-0D0C-4657-9D99-56629CC03CF6 ) | [xp264-000--admin](../../../../actions/workflows/xp264-000-teched-622af3fe-a2f5-4fdd-a05f-73e343aec2a5.yml) | [xp264-000--xp264](../../../../actions/workflows/xp264-000-teched-622af3fe-a2f5-4fdd-a05f-73e343aec2a5-xp264.yml) | [k8s-data-context](../../../../actions/workflows/k8s-data-context-teched.yml)
 | [uk-xp264]() |https://url.sap/tyapw7 | [<img src="../landscape/uk-xp264/kyma_dashboard_url_uk_xp264.png" width="100" />](https://dashboard.kyma.cloud.sap/?kubeconfigID=0FD84322-535C-4047-89CE-47FC775938FC ) | [uk-xp264--admin](../../../../actions/workflows/uk-xp264-teched-76f46b5b-d9ab-486f-8e4f-12e1163af943.yml) | [uk-xp264--xp264](../../../../actions/workflows/uk-xp264-teched-76f46b5b-d9ab-486f-8e4f-12e1163af943-xp264.yml) | [k8s-data-context](../../../../actions/workflows/k8s-data-context-teched.yml)


 
- Each cluster has been configured to the same template with dedicated namespaces for each student.
- As this is an academic exercise, the complete user/namespace isolation has not been enforced.
- Last but not least, all students have accees to the Easy Navigation dashboard, namely:  

<table style="width: 100%; border-collapse: collapse; background-color: #f5f5f5;" border="1">
<tbody>
<tr style="height: 193px;">
<td style="width: 71.6%; height: 193px;">
<div>
<h1><a href="https://url.sap/3kf0ol"><img class="aligncenter" src="../ex0/images/site_navigation.png" alt="site_navigation" height="800"/></a></h1>
</div>
</td>
</tr>
</tbody>
</table>   


- The students do not have access to the master components of the landscape. 
- Any shared infrascture access required for the session is granted via SSO with the links available from the Easy Navigation site.

| Account Name              | Type        |                                                                                                                                Description |
| :------------------------ | :---------: | :------------------------------------------------------------------------------------------------------------------------ |
| btp-argocd                |  Session Master  | with a shared ArgoCD instance (with SSO for all participants)             |
| btp-bootstrap             |  Session Master  | XP264 session bootstrap context for the terraform automation. |
| btp-provider              |  Session Master  | with shared SAP HANA Cloud and Cloud Logging (SAML SSO) services instances.|


## Exercise 0.3 - Solution brief. Funtional architecture

Here goes a diagram of the functional architecture of the solution

<table style="width: 100%; border-collapse: collapse; background-color: #f5f5f5;" border="1">
<tbody>
<tr style="height: 193px;">
<td style="width: 71.6%; height: 193px;">
<div>
<h1><a href="https://url.sap/3kf0ol"><img class="aligncenter" src="../ex0/images/functional_architecture.png" alt=""/></a></h1>
</div>
</td>
</tr>
</tbody>
</table>   


Each student's runtime context has a preconfigured SAP Cloud Connector attached, for instance:


<table style="width: 100%; border-collapse: collapse; background-color: #f5f5f5;" border="1">
<tbody>
<tr style="height: 193px;">
<td style="width: 71.6%; height: 193px;">
<div>
<h1><a href=""><img class="aligncenter" src="https://github.com/user-attachments/assets/5e92690b-41ad-4cf4-993a-f8486d0bb32d" alt="" /></a></h1>
</div>
</td>
</tr>
</tbody>
</table>  

## Summary

Now that you have everything you need to successfully go through this TechEd session:

- A GitHub account.
- Your own fork of the session's GitHub repository.
- Access to the SAP BTP managed kubernetes landscape with the easy navigation site
- An idea of the functional architecture behind the solution brief

Continue to [First things first. Getting to know SAP managed kubernetes runtime](../ex1/README.md)
