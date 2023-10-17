# Set up SSM Agent
# Need for SSM agent:
If EC2 instances created in private subnet and you want to connect to instances without using ssh through jump host or bastion. Then you can use SSM agent. For this we have some steps.

## 1. Enable SSM-agent and check the status of SSM agent.

<img width="791" alt="check status of ssm agent" src="https://github.com/Monachawla1712/Level--2/assets/146841568/cf877856-8d46-48cb-99e1-242b32808348">

In ubuntu 22.04 , ssm is already installed. only we need to enable the service.

(i) first we need to ssh the private instance through jump host and enable the service.
 ### sudo systemctl start snap.amazon-ssm-agent.amazon-ssm-agent.service 
 ### sudo systemctl status snap.amazon-ssm-agent.amazon-ssm-agent.service

 and after enabled the ssm agent come out from ssh.


## 2. Create  an IAM role for EC2 instance and attach this Policy for SSM.
(i) Go to IAM service.
(ii) In the left hand side, click on the role and create role.
<img width="829" alt="iam role for ssm" src="https://github.com/Monachawla1712/Level--2/assets/146841568/66b2f1b2-dbb1-4e2d-9a74-4a1cc35b3bbb">

(iii) In the trusted entity , select AWS Service.
<img width="658" alt="select ec2 service for ssm" src="https://github.com/Monachawla1712/Level--2/assets/146841568/1df7126b-91ba-43bd-a064-c4523fa3a9b3">

(iv) In the use-Case section, choose EC2.
<img width="397" alt="choose ssm" src="https://github.com/Monachawla1712/Level--2/assets/146841568/70ad1d07-01b3-431c-9160-b99e62449c7c">

(V) In the add permission. create policy " AmazonSSMManagedInstanceCore"

<img width="773" alt="choose this policy" src="https://github.com/Monachawla1712/Level--2/assets/146841568/62814a2b-5723-49e4-ad77-fc330cdefafc">

## 3. Attach Policy to all the private instances.
(i) Selec the instance.

(ii) Go to the actions and then in modify IAM role.

(iii) Attach role and update IAM role.
<img width="517" alt="attach it" src="https://github.com/Monachawla1712/Level--2/assets/146841568/ca1f0f40-c702-488b-a964-d0b1683cc860">

## 4. Go to session manager and connect the instance.
<img width="576" alt="connect to ssm manager" src="https://github.com/Monachawla1712/Level--2/assets/146841568/de25e382-80e4-4e43-b495-ee50716d867f">


