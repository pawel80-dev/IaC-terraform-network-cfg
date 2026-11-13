# IaC-terraform-network-cfg  

Based on [Network as Code IOS-XE](https://netascode.cisco.com/docs/start/iosxe/introduction/)  

![alt text](drawings/jenkins_pipeline_v03.png)  
*NaC: generic design*  

Grant Jenkins access to GitLab projects:  
[Create a group access token](https://docs.gitlab.com/user/group/settings/group_access_tokens/#create-a-group-access-token/)  

GitLab <-> Jenkins, webhook integration
[Configure GitLab project](https://docs.gitlab.com/integration/jenkins/)  

Tools:
- Github (single source of truth)
- GitLab (on-premise)
- Terraform provider for IOS-XE
- [Terraform Network-as-Code Cisco IOS-XE Module](https://github.com/netascode/terraform-iosxe-nac-iosxe)
- Terraform cloud (for Terraform state)