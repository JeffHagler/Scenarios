# Anonymous IP walkthrough

## Cited Resources:
[Microsoft: Anonymous IP address](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/howto-identity-protection-simulate-risk#anonymous-ip-address) <br />


## Assumptions:
A login was attempted from a Tor Browser to simulate anonymous IP addresses.  <br />
[License requirements:](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/overview-identity-protection#license-requirements) Microsoft Entra ID P2 (Azure Active Directory P2)


## View video on how a threat actor will use the TOR Browser to obfuscate their identity after acquiring stolen credentials


## View in Entra Identity:
1. Using one of the SOC analyst accounts provided, log in to [Microsoft Entra admin Center](https://entra.microsoft.com/)
2. Click on ID Protection <br />
 ![image](https://github.com/Tungsten66/Scenarios/assets/40893034/990318ee-90e1-496b-8597-9a9f9c6cec12)
3. Click Protection/Identity Protection, then Risk Detections <br />
![Risk Detections](https://github.com/Tungsten66/Scenarios/assets/41757640/b869583f-8c9b-439a-a38f-1f6ee2deb985)
4. In Risk Detections note the one from an Anonymous IP  <br />
![image](https://github.com/Tungsten66/Scenarios/assets/40893034/7241debf-464a-44ac-90af-638919ff0db3)
6. Click on and review the user  <br />
![image](https://github.com/Tungsten66/Scenarios/assets/40893034/c6e75cde-75c8-48ff-a0e5-089589d5c98d)
7. Optionally review Risky Sign-ins <br />
![Risky Sign Ins](https://github.com/Tungsten66/Scenarios/assets/41757640/6bb72fef-cbcf-4ced-93f9-58fa53c47eaa)
8. Optionally review Risky Users <br />
![Risky Users](https://github.com/Tungsten66/Scenarios/assets/41757640/def003c3-12a5-45d8-817b-6a1132ec1f53)
9. Here is where you can Confirm or Dismiss the user risk (DO NOT do this during the demo) <br />
![Confirm or Dismiss Risk](https://github.com/Tungsten66/Scenarios/assets/41757640/ad68ebe3-0327-4496-b0bf-33da11035dc6)


## Instructor demonstration of Analytic Rule Creation:


## View in Microsoft Sentinel:

1. Go to [Azure Portal](https://portal.azure.com/) and Search for Microsoft Sentinel
![Search For Sentinel](https://github.com/Tungsten66/Scenarios/assets/41757640/78a4c3a5-b48a-47d4-b005-609fffe71191)
2.Click on your desired Sentinel Instance
![Desired Instance](https://github.com/Tungsten66/Scenarios/assets/41757640/a70d5627-f7e0-4f65-8794-5cf06f2fb483)
3. Go to Incidents and note the Anonymous IP Address incident
![Anon IP Incident](https://github.com/Tungsten66/Scenarios/assets/41757640/a533d564-8cbf-496b-ae49-d85ea8b300f2)
