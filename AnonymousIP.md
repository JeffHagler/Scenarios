# Anonymous IP walkthrough

## Cited Resources:
[Microsoft: Anonymous IP address](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/howto-identity-protection-simulate-risk#anonymous-ip-address) <br />

## Assumptions:
A login was attempted from a Tor Browser to simulate anonymous IP addresses.  <br />
[License requirements:](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/overview-identity-protection#license-requirements) Microsoft Entra ID P2 (Azure Active Directory P2)

## Instructions:
1. Using one of the SOC analyst accounts provided login to [Microsoft Entra admin Center](https://entra.microsoft.com/)
2. Click on ID Protection <br />
 ![image](https://github.com/Tungsten66/Scenarios/assets/40893034/990318ee-90e1-496b-8597-9a9f9c6cec12)
3. Click Protection <br />
![image](https://github.com/Tungsten66/Scenarios/assets/40893034/62418942-d780-48d5-b5eb-4d9203085d73)
4. Click Identity Protection <br />
![image](https://github.com/Tungsten66/Scenarios/assets/40893034/6e551c2c-19e0-43dc-9752-e5c469269418)
5. Go to Risk Detections  <br />
![image](https://github.com/Tungsten66/Scenarios/assets/40893034/7241debf-464a-44ac-90af-638919ff0db3)
6. Click on and review the user  <br />
![image](https://github.com/Tungsten66/Scenarios/assets/40893034/c6e75cde-75c8-48ff-a0e5-089589d5c98d)

## Post Condition:

> [!NOTE]
> Instructor led

Now lets review how an Incident can be generated in Sentinel by going to Azure Portal https://portal.azure.com
1. Go to Sentinel > Analytics
2. Go to "Rule templates" and search for "Identity Protection"
3. Select and create the rule called "Create incidents based on Azure Active Directory Identity Protection alerts"
4. Accept all defaults and create the rule in the wizard <br />
![image](https://github.com/Tungsten66/Scenarios/assets/40893034/3cc228ce-0c85-4b44-8c11-dc91551e85d2)
3. Go to Sentinel > Incidents to review the new incidents

