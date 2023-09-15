# Anonymous IP walkthrough

## Cited Resources:
[Microsoft: Anonymous IP address](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/howto-identity-protection-simulate-risk#anonymous-ip-address) <br />

## Assumptions:
A login was attempted from a Tor Browser to simulate anonymous IP addresses.

## Instructions:
1. Using one of the SOC analyst accounts provided login to [Microsoft Entra admin Center](https://entra.microsoft.com/)
2. Click on ID Protection <br />
 ![image](https://github.com/Tungsten66/Scenarios/assets/40893034/990318ee-90e1-496b-8597-9a9f9c6cec12)
3. Click Protection <br />
![image](https://github.com/Tungsten66/Scenarios/assets/40893034/62418942-d780-48d5-b5eb-4d9203085d73)
4. Click Identity Protection <br />
![image](https://github.com/Tungsten66/Scenarios/assets/40893034/6e551c2c-19e0-43dc-9752-e5c469269418)
5. Go to Risk Detections  <br />
Enter image here
6. Click on and review the user  <br />
Enter image here



## Post Condition:

Now lets review how an Incident can be generated in Sentinel by going to Azure Portal https://azure.portal.com
1. Go to Sentinel > Analytics - Click on Rule templates and search for "Identity" and select Create incident based on Azure Active Directory and click on Create rule <br />
![image](https://github.com/Tungsten66/Scenarios/assets/40893034/98ad7e32-623f-4840-9d92-722dbd2a5896)
2. Go to Sentinel > Incidents to review the new incidents
3. 

