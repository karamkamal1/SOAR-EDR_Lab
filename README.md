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

![Screenshot (579)](https://github.com/user-attachments/assets/0fa5a038-83df-4dd8-99c2-5341a96d148d)

![Screenshot (580)](https://github.com/user-attachments/assets/4a8b86e1-4a0a-4fab-a2fb-65dea99d28ff)

![Screenshot (584)](https://github.com/user-attachments/assets/2f3601c0-ad21-4491-853a-724911fbac1c)

![Screenshot (594)](https://github.com/user-attachments/assets/298c3d1f-b1fe-4344-930e-e027c3c8f28c)

![Screenshot (600)](https://github.com/user-attachments/assets/a4f06256-ebb8-4da7-92cc-0f629465265c)

![Screenshot (603)](https://github.com/user-attachments/assets/b1b58cc3-46f4-4b7f-bda9-b09ba0560b09)

![Screenshot (604)](https://github.com/user-attachments/assets/9d587e28-c394-4a8c-accb-8e1daa0a8922)

![Screenshot (606)](https://github.com/user-attachments/assets/019e3f77-7d23-4274-9ef3-ff3f1cfa1d7b)

![Screenshot (631)](https://github.com/user-attachments/assets/815e6323-17c9-4f80-93f1-1c414fa6f3c3)

![Screenshot (638)](https://github.com/user-attachments/assets/51556df1-6557-43f8-8948-90384de0e9a1)

![Screenshot (639)](https://github.com/user-attachments/assets/4a144b7e-62fa-400f-a8d2-03888b6b4722)

![Screenshot (644)](https://github.com/user-attachments/assets/f95f2d63-8217-475c-9a7b-5f2c2e8aaa2d)

![Screenshot (652)](https://github.com/user-attachments/assets/5fb5cab7-7a2d-4789-bd85-7e1b1bb1ed03)

![Screenshot (653)](https://github.com/user-attachments/assets/3239d14b-6109-4917-a2d1-f87108f7a899)

![Screenshot (655)](https://github.com/user-attachments/assets/1e7b99cd-1eb7-4f42-9b82-055fac2244fe)

![Screenshot (659)](https://github.com/user-attachments/assets/7e0ec828-a959-4a97-9ae0-e4180e24951c)

![Screenshot (661)](https://github.com/user-attachments/assets/ad51ba96-6466-4a9c-8682-5b01917021e3)

![Screenshot (663)](https://github.com/user-attachments/assets/16932b62-0e90-43f0-9214-cbd424555827)

![Screenshot (666)](https://github.com/user-attachments/assets/4c7ef42b-3dd2-45ea-9c1c-8232fc72070c)

![Screenshot (676)](https://github.com/user-attachments/assets/e38e74fd-28be-4eb8-9a4c-ba1d26471129)

![Screenshot (677)](https://github.com/user-attachments/assets/a9b2da1b-417e-425b-ad49-8bf933fc6094)

![Screenshot (680)](https://github.com/user-attachments/assets/95cbf60a-3760-4e55-b5fc-df3830362f60)

![Screenshot (682)](https://github.com/user-attachments/assets/747e6a97-05ef-4d91-a1ae-8dc066cfcab8)

![Screenshot (685)](https://github.com/user-attachments/assets/2f4364f5-8e1f-4834-aa99-0f9b95ae935d)

![Screenshot (691)](https://github.com/user-attachments/assets/f04b5cfe-1d62-44aa-a20c-33c204195b62)

![Screenshot (693)](https://github.com/user-attachments/assets/2465d7a1-6ba0-4603-985b-794135e4e8cf)

![Screenshot (694)](https://github.com/user-attachments/assets/287cbea9-d7d9-4270-ad45-57340491e30c)

![Screenshot (698)](https://github.com/user-attachments/assets/d329f7d2-fc13-4411-9f6e-d9c63177c7d6)

![Screenshot (699)](https://github.com/user-attachments/assets/bc230493-37d8-402f-932d-94dd2bf60978)

![Screenshot (704)](https://github.com/user-attachments/assets/6513f2d0-63c1-4521-a1c7-3fbc419ee2b6)

![Screenshot (722)](https://github.com/user-attachments/assets/c4726fc9-0c4b-417a-a664-4be32ec1f849)

![Screenshot (725)](https://github.com/user-attachments/assets/aacd627a-cd5b-4bed-88a2-6d6a8342fffd)

![Screenshot (735)](https://github.com/user-attachments/assets/dad48d97-1f56-4ad7-8d1a-12159d8d8d5f)

![Screenshot (739)](https://github.com/user-attachments/assets/88bf7a97-928d-4c76-b601-bbe284894844)

![Screenshot (740)](https://github.com/user-attachments/assets/d8e976f1-6c9e-41b2-a010-0b1f4384d773)

![Screenshot (747)](https://github.com/user-attachments/assets/932441cd-82f8-4ced-a13b-4257d34e4fdd)

![Screenshot (750)](https://github.com/user-attachments/assets/54718e7a-12d0-4a79-a060-9e66c3079672)

![Screenshot (756)](https://github.com/user-attachments/assets/023fb204-3530-4416-831c-81ace1f2ea99)

![Screenshot (758)](https://github.com/user-attachments/assets/170875ce-9e5a-47be-ad3d-1c2e88b3c265)

![Screenshot (761)](https://github.com/user-attachments/assets/6e2d1dde-dcea-47f3-9987-66b8f46bdea2)

![Screenshot (763)](https://github.com/user-attachments/assets/27e6b629-99ce-4eca-9547-26736d00460c)

![Screenshot (764)](https://github.com/user-attachments/assets/99db5483-4270-40f1-b745-2d030d23dc97)

![Screenshot (765)](https://github.com/user-attachments/assets/2d8903c8-e67a-4760-8562-0fe662f08e10)

![Screenshot (773)](https://github.com/user-attachments/assets/5ff67ace-6bfa-4a14-8924-099f72173d83)

![Screenshot (780)](https://github.com/user-attachments/assets/94e67d88-0143-41cf-bda8-78eddcd89728)

![Screenshot (785)](https://github.com/user-attachments/assets/d3b50df7-209c-4843-82ba-76986334681d)

![Screenshot (786)](https://github.com/user-attachments/assets/7e7aeab3-eb9a-45b0-aaf6-fdd6ed1fb34e)

![Screenshot (796)](https://github.com/user-attachments/assets/78167f8d-1e84-4c2b-8f44-c9dea8a6c906)

![Screenshot (799)](https://github.com/user-attachments/assets/8cefda03-7bf7-41a9-9d1b-e17cd981b2f3)

![Screenshot (800)](https://github.com/user-attachments/assets/4f8a1e76-0798-4b7a-80dc-ab49a3ad059d)

![Screenshot (801)](https://github.com/user-attachments/assets/f2053c6a-2296-4380-8242-1ca269973077)

![Screenshot (805)](https://github.com/user-attachments/assets/649cac0c-0a77-41ca-bc97-9eb1c2249360)

![Screenshot (813)](https://github.com/user-attachments/assets/418714b6-d08e-449a-8470-d9e0fcd6e32c)

![Screenshot (816)](https://github.com/user-attachments/assets/e8addf32-0ac4-4513-9a72-bd3b9f998499)

![Screenshot (819)](https://github.com/user-attachments/assets/aaf06a87-3cc1-4751-9f66-2ad46140e2f4)

![Screenshot (824)](https://github.com/user-attachments/assets/011438af-b867-434c-adce-7698b30e7208)

![Screenshot (826)](https://github.com/user-attachments/assets/0857dcee-bff2-4cef-8243-005033d8eb09)

![Screenshot (825)](https://github.com/user-attachments/assets/9c976160-eaea-4c2d-a749-ec51103ebfd2)

![Screenshot (827)](https://github.com/user-attachments/assets/e41c83a6-04d2-426d-b055-8ccc8b5b641f)

![Screenshot (828)](https://github.com/user-attachments/assets/de9349be-76cb-4d30-a6ea-f4f7ad4104f3)

![Screenshot (829)](https://github.com/user-attachments/assets/345636c0-475b-42df-afa0-9258de4d8bc0)

![Screenshot (830)](https://github.com/user-attachments/assets/5b50b607-745d-48a4-9b58-a7016b225ac1)

![Screenshot (831)](https://github.com/user-attachments/assets/9d7a05f2-71d1-4d3e-bb8e-bf0b69ab566e)

