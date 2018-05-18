# Security-multi-stage-data-analysis

Introduction
The goal of this project is to understand the progression of a multi-stage attack that aims to leak secret keys from target system. In this project, you will perform analysis of a multi-stage attack recreated from publicly available information on the Equifax breach. You will explore the use of signature-based, anomaly-based, and factor graph-based techniques.
As a defender, you are given monitoring logs to perform the following tasks:
Compare the attacker’s behavior vs. legitimate users’ behavior (Task 1)
Build a simple factor graph for a single event and a single attack stage (Task 2)
Extend the factor graph to capture the evolution of a series of events (Task 3)
Run inference on attack stages using the extended factor graph (Task 3)

As a defender, you are given monitoring logs to perform the following tasks:

Compare the attacker’s behavior vs. legitimate users’ behavior (Task 1)
Build a simple factor graph for a single event and a single attack stage (Task 2)
Extend the factor graph to capture the evolution of a series of events (Task 3)
Run inference on attack stages using the extended factor graph (Task 3)

Attacker Actions
Stages 1-2 The attack starts in the discovery stage (1), where an attacker repetitively scans for vulnerable Apache Struts portals (CVE-2017-5638). These scans do not require immediate action from security operators because the scans have not affected the system. The attack then progresses to the access stage (2) where the attacker obtains a remote shell terminal by exploiting the vulnerability (CVE-2017-5638).
Stages 3-4 After establishing a foothold in the system, the attacker executes commands with superuser permissions (i.e., the privilege escalation stage (3)) as the web server runs with as root. The attacker proceeds to the persistence stage (4), where he/she downloads a file with a sensitive extension, e.g., .c, which is commonly seen in both legitimate users and malicious activities. The file contains a rootkit that will be installed as a new system service, i.e., a kernel module. At this persistence stage (4), the ongoing attack needs an immediate defensive response since the attacker can maintain persistent access to the compromised system using a backdoor which provides a secret communication channel, i.e., DNS tunneling.
Stages 5-7 The attacker then collects secret keys, i.e., Secure Shell keys such as RSA keys in the collection stage (5). Using the backdoor, the attacker sends additional commands in the command & control stage (6) to establish a DNS tunnel. Then, the secret keys are extracted in the exfiltration stage (7).
