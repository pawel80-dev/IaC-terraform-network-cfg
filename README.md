# IaC-terraform-network-cfg  

Based on [Network as Code IOS-XE](https://netascode.cisco.com/docs/start/iosxe/introduction/)  

![alt text](drawings/jenkins_pipeline_v03.png)  
*NaC: generic design*  

Grant Jenkins access to GitLab projects:  
[Create a group access token](https://docs.gitlab.com/user/group/settings/group_access_tokens/#create-a-group-access-token/)  

GitLab <-> Jenkins, webhook integration
[Configure GitLab project](https://docs.gitlab.com/integration/jenkins/)  

Add Jenkins agent as Podman container:  
• Navigate to Nodes. Go to **Manage Jenkins > Nodes** (or Manage Nodes and Clouds) and click **New Node**  
• Name the agent. Enter a descriptive name (such as agent2_podman), select **Permanent Agent**, and click **Create**  
• Set the root directory. Enter /home/jenkins/agent in the Remote root directory field  
• Add labels. Type a label like **podman2** or linux so your Jenkinsfile pipelines can target this specific agent  
• Select the launch method. Choose Launch agent by connecting it to the controller. Checking Use WebSocket is recommended so the agent communicates over your standard HTTP/HTTPS port (8080) without requiring a separate TCP port (50000)  
• Copy the secret. Click Save, **click on your newly created node in the list**, and copy the secret key shown in the example command   

Execute below command on Podman server:  
```podman run -d --name agent2_podman --restart unless-stopped --init -v jenkins-agent-workdir:/home/jenkins/agent docker.io/jenkins/inbound-agent:latest -url http://jenkins.homelab.com:8080 -webSocket -secret a958e5d3aab0e68e4bfaf81915ed1d8dce20411c8e767c3b9585ec539ca00647 -name "agent2_podman"```  

> [!NOTE]
> Usefull Podman commands:  
> podman ps       # This command is used to list the running containers  
> podman ps -a    # This command is used to show all the running and exited containers  
> podman stop <container-name> # This command stops a running container  
> podman rm <container-name>   # This command is used to delete a stopped container  

> [!NOTE]
> Gitlab: check Webhooks send to Jenkins  
> Jenkins: check Triggers  

Tools:
- Github (single source of truth)
- GitLab (on-premise)
- Terraform provider for IOS-XE
- [Terraform Network-as-Code Cisco IOS-XE Module](https://github.com/netascode/terraform-iosxe-nac-iosxe)
- Terraform cloud (for Terraform state)