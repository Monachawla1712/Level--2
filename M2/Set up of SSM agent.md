# Set up SSM Agent
# Need for SSM agent:
If EC2 instances created in private subnet and you want to connect to instances without using ssh through jump host or bastion. Then you can use SSM agent. For this we have some steps.

## 1. Enable SSM-agent and check the status of SSM agent.

<img width="791" alt="check status of ssm agent" src="https://github.com/Monachawla1712/Level--2/assets/146841568/cf877856-8d46-48cb-99e1-242b32808348">

In ubuntu 22.04 , ssm is already installed. only we need to enable the service.

(i) first we need to ssh the private instance through jump host and enable the service.
 ## sudo systemctl start snap.amazon-ssm-agent.amazon-ssm-agent.service
## sudo systemctl status snap.amazon-ssm-agent.amazon-ssm-agent.service

 and after enabled the ssm agent come out from ssh.


## 2. Create  an IAM role for EC2 instance and attach this Policy for SSM.
(i) Go to IAM service.
(ii) In the left hand side, click on the role and create role.
(iii) In the trusted entity , select AWS Service.
(iv) In the use-Case section, choose EC2.
(V) In the add permission. create policy " AmazonSSMManagedInstanceCore"

## 3. Attach Policy to all the private instances.
(i) Selec the instance.
(ii) Go to the actions and then in modify IAM role.
(iii) Attach role and update IAM role.

## 4. Go to session manager and connect the instance.


