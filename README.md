Infrastructure Project Notes

Requirements:
Global + Fast: North America & Europe, low latency
Cheap: Under $5/month at low traffic
IaC: Terraform automated deploy/teardown
Day 2 Ready: Monitoring, logs, secrets, team handover
------------------------------------------------------

Architecture Analysis:

Global CDN: Azure Static Web Apps = automatic global distribution
Security: Managed Identity + Federated credentials(GitHub -> Azure connection) + GitHub secret store inventory = no secrets in code
Monitoring: Application Insights with availability tests and error logging
IaC Complete: Terraform automation with CI/CD pipeline. Written in for_each welcomes the next feature

Git Repository:

Infra configuration tf files: https://github.com/PranayKrishnaS/acme-iac-infra.git
Terraform modules: https://github.com/PranayKrishnaS/modules.git/azurerm 
Sample application: https://github.com/PranayKrishnaS/acme-ads-prod-project.git
CI/CD: https://github.com/PranayKrishnaS/modules.git/terraform_workflow_template.yml

Running endpoint: https://witty-hill-0fdffa61e.2.azurestaticapps.net

Architecture diagram:

<img width="1214" height="1000" alt="image" src="https://github.com/user-attachments/assets/85ee71d5-67d4-4439-8f87-a64cc80bebf3" />

Cost calculation & assumptions:

Service	Tier	                        Monthly Est.
Azure Static Web Apps	Free	          $0.00
Application Insights	Free	          ~$0.25
Log Analytics (basic use)	Free	      ~$0.30–0.40
Terraform state storage	Standard	    ~$0.10

Operational considerations:

Checkov Scanning
GitHub Secret store
Least privilege access

Optional extras:
Application insights - for metrics, availability, Transactional Search



