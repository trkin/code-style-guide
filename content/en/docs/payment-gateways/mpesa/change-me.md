---
title: "MPESA API"
linkTitle: "MPESA API Check transaction"
weight: 100
description: >-
     MPESA api check transaction
---

API check transaction status https://developer.safaricom.co.ke/apis/TransactionStatus

The Initiator is the API user username created on M-Pesa Portal and SecurityCredential is encrypted API user password.

Kindly follow below a step-by-step process for creating API operator/initiator and setting their password:

 

## Step 1: Create a Business Manager

Login on MPESA portal, https://org.ke.m-pesa.com/ as the Business administrator
Click on Search, Then Organization operator.
Then click the +Create 
It will take you to a new page where you select access channel as Web
Enter the Username of the operator,
Then select web profile default rule profile
Then assign role...Business Manager and Set Restricted ORG API PASSWORD.
Enter the KYC information of the operator then submit

 

## Step 2: Create an API operator 

Log in as the Business administrator
Click on Search, Then Organization operator.
Then click the +Create 
Select access channel as API
Enter the Username
rule profile
Then assign role 
Enter the KYC information of the operator then submit

 

## Step 3: Setting the API users' password 

Login on MPESA portal as user with the Set Restrict Password Role i.e. The Business Manager
Click on Search, Then Organization operator.
Enter the API username to search after it populates the API user, At the end click on Operation Detail
Then click on Set Password.
