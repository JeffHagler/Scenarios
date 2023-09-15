# Password Spray walkthrough

## Cited Resources:
[Microsoft Security Blog: Protecting your organization against password spray attacks](https://www.microsoft.com/en-us/security/blog/2020/04/23/protecting-organization-password-spray-attacks/) <br />
[Error code lookup tool](https://login.microsoftonline.com/error)

## Assumptions:

The Azure Active Directory solution is installed from the Sentinel Content hub
The Azure Active Directory Diagnostics settings have been configured to send SignInLogs to the Sentinel Log Analytics workspace


## Instructions:
1. Open a new InPrivate window in Microsoft Edge
2. Using one of the demo user accounts provided attempt to login to https://portal.azure.com five or more times with the wrong password
3. Using one of the SOC analyst accounts provided login to [Microsoft Entra admin Center](https://entra.microsoft.com/)
4. In the Microsoft Entra admin center go to Sign-in events by clicking on Identity > Monitoring & health > Sign-in logs
5. Add a filter to look for our demo user that we tried to login to the portal with the wrong password five or more times.
6. Click on Add Filters, select User and click Apply.<br />
![image](https://github.com/Tungsten66/Scenarios/assets/40893034/8bd0cf43-72c3-4fd9-8ba8-f1dfb97b3b0f)
7. Type the username into field and click Apply <br />
![image](https://github.com/Tungsten66/Scenarios/assets/40893034/9f1ac69a-6adb-42dd-bfbf-f5708dbdc199)
8. See all the Failures for the demo user
![image](https://github.com/Tungsten66/Scenarios/assets/40893034/526964ef-a9fd-43dd-b89b-e525f23328aa)
9. Click on one of the failures and capture the Sign-in error code
![image](https://github.com/Tungsten66/Scenarios/assets/40893034/4ef8f046-1478-4a6c-b275-ffbc0148f561)
10. With the SOC analyst account login to https://portal.azure.com/
11. Go to Sentinel > Logs
12. Now write the KQL to search for users that have tried to login into the Azure Portal five or more times using the previously captured Sign-in error code
```console
SigninLogs
| where AppDisplayName == "Azure Portal"
| where ResultType == "50126"
| summarize count() by UserPrincipalName
| where count_ > 4
```
![image](https://github.com/Tungsten66/Scenarios/assets/40893034/3759eb42-095e-4446-a4ca-fbc66a302fe2)



## Post Condition:

Create an analytic rule to generate an incident when the above indicator of compromise occurs.

1. Under Sentinel > Analytics - Create a Scheduled query rule
![image](https://github.com/Tungsten66/Scenarios/assets/40893034/fb9ba7c7-4252-4003-91fd-2d2a16dda4fa)
2. Paste in the KQL into teh Rule Query,  update the Entity mapping, and update your Query scheduling
![image](https://github.com/Tungsten66/Scenarios/assets/40893034/55e7974b-26c5-4c9c-b977-f50f447bdc8a)
![image](https://github.com/Tungsten66/Scenarios/assets/40893034/a17621b0-193b-4fae-817d-6d5a22857f8f)
4. Review new incident
![image](https://github.com/Tungsten66/Scenarios/assets/40893034/c4d72e71-db17-4ec0-980c-980ba5010338)



