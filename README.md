## Infrastructure as Code (IaC) - Terra Form


<img width="741" alt="image" src="https://github.com/MutiatOba/iac_terraform/assets/118978642/a4400756-cf8c-4e63-8512-f67ba749d185">

### Initial steps to set up Terra Form

1. Check if you have terraform installed: ```terraform --version```
2. if you dont have the latest version, follow the steps here to install terraform: https://developer.hashicorp.com/terraform/downloads
3. create an enviromement variable for your aws secrete key and access key. make sure you set it as a user variable (so only the specific user has access to the keys). Here is how to create an enviroment variable: https://docs.oracle.com/en/database/oracle/machine-learning/oml4r/1.5.1/oread/creating-and-modifying-environment-variables-on-windows.html#GUID-DD6F9982-60D5-48F6-8270-A27EC53807D0
4. Need to create a main.tf: 
- need to let terraform know who is on the other end - we will use AWS
- need to connect to be authorised to connect to AWS - aws keys set up as ENV variable
- download dependencies required 

### Creating your main.tf file

Head over to your gitbash (as admin):

- type: ```nano main.tf```
<img width="371" alt="image" src="https://github.com/MutiatOba/iac_terraform/assets/118978642/9aa9e3dd-70bd-4e6f-9b3d-4c80c2cd710d">

- ```terraform init``` - initialise terraform
- to create a service type: ```nano main.tf``` and update the file as follows:
<img width="446" alt="image" src="https://github.com/MutiatOba/iac_terraform/assets/118978642/0c0928b6-f335-4c56-9ba9-fb9775602667">

- type ```terraform plan``` this execute the file and checks validation
- this executes the file: ```terraform apply```. You should see your instance ruuning on aws
- run ```terraform destroy``` to destroy your resources 


### Creating a variable

- create a file called: variable.tf and save it in a file called .gitignore
- add the following information to your .gitignore file:

<img width="390" alt="image" src="https://github.com/MutiatOba/iac_terraform/assets/118978642/8e57b0c9-652e-4bad-a173-4730822b7d33">

- add the following information to your variable.tf file:

<img width="352" alt="image" src="https://github.com/MutiatOba/iac_terraform/assets/118978642/d03e91de-e6b3-4c1d-96e3-353078370d0b">

- makes the following amendment to your main.tf file to include reference to the:
<img width="375" alt="image" src="https://github.com/MutiatOba/iac_terraform/assets/118978642/07cc3ec5-00c8-42a6-a704-50c2f375e5cf">

- type ```terraform apply``` then your instance should be able to see your instance running 

### Creating VPC with terraform

<img width="688" alt="image" src="https://github.com/MutiatOba/iac_terraform/assets/118978642/e79abb47-7270-4951-9b30-6032a85f5695">

steps:
1. create a vpc with CIDR block
2. create ig and attach to vpc
3. create public subnet in vpc with CIDR block, 
4. create a public route table route table [allows traffic inside vpc and ig] attach it to public subnet
5. create a security group for ec2 [allows traffic from ports 22, 80 and 3000] attach it to the ec2 instance

Your main.tf should look like so:
<img width="249" alt="image" src="https://github.com/MutiatOba/iac_terraform/assets/118978642/ed298bf9-e5ad-4f85-b511-24f410500e98">
<img width="208" alt="image" src="https://github.com/MutiatOba/iac_terraform/assets/118978642/398fbe93-e8c6-4345-9e89-8fb6caf5dd12">
<img width="247" alt="image" src="https://github.com/MutiatOba/iac_terraform/assets/118978642/13675ae5-c4df-48cd-b3d4-b97a8219305b">
<img width="224" alt="image" src="https://github.com/MutiatOba/iac_terraform/assets/118978642/89f6439c-f9e5-4db9-a0fb-0f5f2a46e2bc">

type in ```terraform apply``` to create the resources



