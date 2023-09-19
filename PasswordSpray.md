# Password Spray walkthrough

## Cited Resources:
[Microsoft Security Blog: Protecting your organization against password spray attacks](https://www.microsoft.com/en-us/security/blog/2020/04/23/protecting-organization-password-spray-attacks/) <br />
[Error code lookup tool](https://login.microsoftonline.com/error)

## Assumptions:

The Azure Active Directory solution is installed from the Sentinel Content hub <br />
The Azure Active Directory Diagnostics settings have been configured to send SignInLogs to the Sentinel Log Analytics workspace


## Instructions:

> [!NOTE]
> Prior to this session the instructors attempted to log in with a demo account 10 times with the wrong password
1. Using one of the demo user accounts provided login to [Microsoft Entra admin Center](https://entra.microsoft.com/)
2. In the Microsoft Entra admin center go to Sign-in events by clicking on Identity > Monitoring & health > Sign-in logs
![Sign In Logs](https://github.com/Tungsten66/Scenarios/assets/41757640/757dec7a-3556-487b-9d72-caa9a4d6d067)
3. To find the user, click on Add filters, select Username and click Apply.<br />
![image](https://github.com/Tungsten66/Scenarios/assets/40893034/8bd0cf43-72c3-4fd9-8ba8-f1dfb97b3b0f)
4. Type the username into the field and click Apply <br />
![image](https://github.com/Tungsten66/Scenarios/assets/40893034/9f1ac69a-6adb-42dd-bfbf-f5708dbdc199)
5. See all the Failures for the demo user
![image](https://github.com/Tungsten66/Scenarios/assets/40893034/526964ef-a9fd-43dd-b89b-e525f23328aa)
6. Click on one of the failures and capture the Sign-in error code
![image](https://github.com/Tungsten66/Scenarios/assets/40893034/4ef8f046-1478-4a6c-b275-ffbc0148f561)
7. Login to [Azure Portal](https://portal.azure.com/)
8. Go to Sentinel, select Logs, and close the first window that appears  
![Sentinel Logs](https://github.com/Tungsten66/Scenarios/assets/41757640/57c56a9b-d534-4b63-a781-db0326440664)

9. Write the KQL query to search for users that have tried to login into the Azure Portal five or more times using the previously captured Sign-in error code 
```console
SigninLogs
| where AppDisplayName == "Azure Portal"
| where ResultType == "50126"
| summarize count() by UserPrincipalName
| where count_ > 4
```
10. Run the query and review the results <br />
![image](https://github.com/Tungsten66/Scenarios/assets/40893034/3759eb42-095e-4446-a4ca-fbc66a302fe2)



## Post Condition:

> [!NOTE]
> Instructor led

Generate an incident in Sentinel by creating an analytic rule to generate an incident when the above indicator of compromise occurs.

1. Under Sentinel > Analytics - Create a Scheduled query rule
![image](https://github.com/Tungsten66/Scenarios/assets/40893034/fb9ba7c7-4252-4003-91fd-2d2a16dda4fa)
2. Paste in the KQL into the Rule Query, update the Entity mapping, and update your Query scheduling
![image](https://github.com/Tungsten66/Scenarios/assets/40893034/55e7974b-26c5-4c9c-b977-f50f447bdc8a)
![image](https://github.com/Tungsten66/Scenarios/assets/40893034/a17621b0-193b-4fae-817d-6d5a22857f8f)
4. Review new incident
![image](https://github.com/Tungsten66/Scenarios/assets/40893034/c4d72e71-db17-4ec0-980c-980ba5010338)
