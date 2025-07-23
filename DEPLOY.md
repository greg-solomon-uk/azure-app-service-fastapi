1. Deploy to Azure
| **Name**                         | **Value**                                 |
|----------------------------------|-------------------------------------------|
| **Subscription**                 | add95dae-484b-4544-ab56-34d373a7b80b       |
| **Resource Group**               | rg_greg                                    |
| **App Name**                     | green-fields                               |
| **Secure Unique Hostname**       | Enabled                                    |
| **Publish**                      | Code                                       |
| **Runtime Stack**                | Python 3.13                                |
| **App Service Plan Name**        | ASP-rggreg-81d6                            |
| **Operating System**             | Linux                                      |
| **Region**                       | UK South                                   |
| **SKU**                          | Basic                                      |
| **Size**                         | Small                                      |
| **ACU**                          | 100 total ACU                              |
| **Memory**                       | 1.75 GB                                    |
| **Application Insights**         | Not enabled                                |
| **Basic Authentication**         | Disabled                                   |
| **Continuous Deployment**        | Enabled                                    |
| **GitHub Account**               | greg-solomon-uk                            |
| **Organization**                 | greg-solomon-uk                            |
| **Repository**                   | azure-app-service-fastapi                  |
| **Branch**                       | main                                       |
| **Database Server Name**         | green-fields-server                        |
| **Database Engine**              | PostgreSQL - Flexible Server               |
| **Compute Tier and Size**        | GeneralPurpose Standard_D2s_v3             |
| **Database Name**                | green-fields-database                      |
| **Database Region**              | UK South                                   |
| **Database Username**            | wygukoxtko                                 |
| **Database Password**            | ****************                           |
| **Virtual Network**              | vnet-wckfblez (10.0.0.0/16)                |
| **Outbound Subnet**              | subnet-qkbtyyoj (10.0.1.0/24)              |

2. **Set the startup command in the portal**
Settings -> Configuration -> Startup Command
gunicorn -w 2 -k uvicorn.workers.UvicornWorker -b 0.0.0.0:8000 main:app


2. **Apply Access Restrictions (IP Whitelisting)**
Go to App Service > Networking > Access Restrictions.
Add rules to allow only your IP or your organization's IP range.
Once a rule is added, all other traffic is implicitly denied.

3. **Enable Authentication (Easy Auth)**
Go to App Service > Authentication.
Add an identity provider (e.g., Microsoft, GitHub, Google).
Set Unauthenticated requests to:
Log in with... (to redirect to login), or
HTTP 401 (to block unauthenticated users).
