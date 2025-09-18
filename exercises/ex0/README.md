# Exercise 0 - Preparation Steps

In this exercise, you will create your own copy of this repository and optionally, set up a GitHub account.

Finally you will login to for this session prepared BTP account.

## Exercise 0.0 - (Optional) Create a GitHub account

1. Navigate to [GitHub](https://github.com/).

2. Click **Sign up for GiHhub**.

3. Alternatevly, click on **Continue with Google** to sign up using social login.

4. Follow the prompts to create your personal account.

## Exercise 0.1 - Create a Copy of This Repository

1. Login to [GitHub](https://github.com/).

2. On the [main page of this repository](https://github.com/SAP-samples/teched2025-XP266), choose **Fork** on the top right.

   <br>![](../ex0/images/fork_entry.png)

3. Make sure that the **Owner** matches the GitHub account that you want to use for this session. All the other information can remain the same.

   <br>![](../ex0/images/fork_details.png)

4. Choose **Create Fork**. You are now brought to a copy of the repository in your GitHub account.

## Exercise 0.2 - Discover your BTP landscape

1. Navigate to the [SAP Business Technology Platform - Cockpit](https://account.hana.ondemand.com/#/home/welcome)

2. Click "Sign In" and enter the for this session provided user credentials

3. After the BPT Cockpit has been loaded, you should see following account structure:

| Account Name              | Type        |                                                                                                                                Description |
| :------------------------ | :---------: | :----------------------------------------------------------------------------------------------------------------------------------------- |
| XP266_CALM                |  Shared     | This BTP subaccount includes are instance of SAP Cloud ALM, which will be shared by all participants of this hands-on session.             |
| XP266_CENTRAL             |  Deticated  | The BTP subaccount named **CENTRAL** contains central services and acts as an central administrative subaccount.                           |
| XP266_DEV                 |  Deticated  | In this BTP subaccount **DEV** development is done. It contains instances of SAP Build, SAP Content Agent services and SAP Mobile Services.|
| XP266_QA                  |  Deticated  | **QA** is one of the target BTP subaccounts where transport requests will be deployed to during this session.                              |
| XP266_PROD                |  Deticated  | **PROD** is one of the target BTP subaccounts where transport requests will be deployed to during this session.                            |

## Summary

Now that you have everything you need to successfully go through this TechEd session:

- A GitHub account.
- Your own fork of the session's GitHub repository.
- A BTP global account with prepared subaccounts.

Continue to [BTP Kyma easy with kyma CLI](../ex1/README.md)