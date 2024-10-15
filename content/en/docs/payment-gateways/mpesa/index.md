---
title: MPesa"
linkTitle: "MPesa"
weight: 2
description: >-
     MPesa Daraja Safaricom
---

## Setup

On Mpesa MyApps page [https://developer.safaricom.co.ke/MyApps](https://developer.safaricom.co.ke/MyApps) click on "CREATE NEW APP",
use arbitrary name, select ALL products and click on "CREATE APP".
![Screenshot 2024-10-15 at 17 17 09](https://github.com/user-attachments/assets/8e58369c-e1cd-4ea9-9cc3-8e61c48ef88a)

Find the created app and click on copy icon to copy "Consumer Key" and "Consumer Secret"

![Screenshot 2024-10-15 at 17 22 12](https://github.com/user-attachments/assets/0ab76730-99b2-464b-bea4-6ab30c49a8ef)

On Xceednet Location Settings click on tab "Payment Gateway" and click on "Edit". Enable "Allow Renewal By Online Payment" and 
select "M-Pesa STK Push". Paste "Consumer Key" and "Consumer Secret" and click "Save"

![Screenshot 2024-10-15 at 17 26 20](https://github.com/user-attachments/assets/35cc4bf9-e94c-4741-8d53-2e5d32d5629b)

If there is an error than check the credentials "Consumer Key" and "Consumer  Secret".
![Screenshot 2024-10-15 at 17 37 07](https://github.com/user-attachments/assets/23ad5619-c729-46b1-ac52-176aa18c783f)

If there is no error on save than credentials are correct.

In order to receive webhooks we need to call API to "add c2b register url". Click "Edit" and select "YES" under "Mpesa add c2b register url"

![Screenshot 2024-10-15 at 17 39 15](https://github.com/user-attachments/assets/9e05d16f-f483-45bc-ae74-f05245101b2d)


In Sandbox mode you can "Mpesa add c2b register url" multiple times, but in production mode, you need to contact MPesa api support to clear old
confirmation and validation URL and than select "Mpesa add c2b register url" and save, and contact MPesa api support to enable newly 
added URLs.
