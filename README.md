# IaC-terraform-network-cfg  

Based on [Network as Code IOS-XE](https://netascode.cisco.com/docs/start/iosxe/introduction/)  

![alt text](drawings/jenkins_pipeline_v03.png)  
*NaC: generic design*

Tools:
- Github (single source of truth)
- GitLab (on-premise)
- Terraform provider for IOS-XE
- [Terraform Network-as-Code Cisco IOS-XE Module](https://github.com/netascode/terraform-iosxe-nac-iosxe)
- Terraform cloud (for Terraform state)