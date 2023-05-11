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
- -run ```terraform destroy``` to destroy your resources 
