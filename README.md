# Security Orchestration Automation and Response Lab

## Objective

The objective of this lab is to create a SOAR (Security Orchestration, Automation, and Response) playbook that automates the detection and response to a malicious event. In this case the playbook will use a LimaCharlie detection rule that triggers when the Lazagne credential harvester is executed on a client on the network. Once triggered, Tines will automatically send a message over Slack and email, including key identifiers of the attack as well as information about the compromised system. Additionally, a user prompt will provide the option to either isolate the infected machine from the network or keep it connected. If the machine is isolated, a confirmation will be sent to verify the successful isolation of the infected computer.

### Diagram

![Soar_Edr_project](https://github.com/user-attachments/assets/25305a3e-c0f3-4bba-9a8c-4d56d39830c1)

### Skills Learned

- Understanding of design and implementation of SOAR Playbooks.
- Enhanced knowledge in writing Detection rules for LimaCharlie.
- Intermediate Knowledge of Tines Automation.
- Enchanced skills in Workflow Automation.
- Gained Practical knowledge of Security Awareness and Endpoint Isolation.

### Tools Used

- LimaCharlie: For Endpoint detection and response (EDR) as well as creating and implementing   
               detection rules. Also used for Endpoint Isolation.
- Tines: For Orchestrating Automated Workflows
- Slack/Email: Recieve real time alerts

## Explanation
drag & drop screenshots here or use imgur and reference them using imgsrc

Every screenshot should have some text explaining what the screenshot is about.

Example below.

*Ref 1: Network Diagram*
