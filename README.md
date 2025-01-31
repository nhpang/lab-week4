**Instructions on general setup**

cloud-config.yaml setup
- this file can be configured by defining the users and packages to install
- be sure to include a public key so you can access the instance later

main.tf setup
- the main.tf file is consisted of many blocks
- each block has it's data source (terraform, provider, locals, resource... etc)
    - terraform will configure any terraform behaviours
    - provider block will configure any provider settings
    - locals block will define all local variables
    - resources block will define any aws resources
        - within resources block, you will define any aws Data Sources, such as 'aws_instance'
        - following the data source will be the your name for the data source
```
resource "aws_instance" "web" {
	#this is an example
    subnet_id = example
    security_groups = [example]
}
```
- once you have defined each part of your instance, such as security groups and vpcs, your main.tf file should be complete

**Command used to create a new SSH key pair**

Command- 'ssh-keygen -b 2048 -t rsa'

This command can be used to create a SSH key.

You will create a public key (defined by the .pub extension) and a private key (with the name provided, id_rsa is the default name).

The public key's content can be placed within the cloud-config.yaml file.

The private key will then be saved and accessed whenever the user would like to enter any instance with it's corresponding public key.

**Commands used to initialize, fmt, plan... configuration**

Command- 'terraform init'
- this command will initialize terraform by downloading provider plugins
  
Command- 'terraform plan'
- If there are any errors within your terraform file, it will be stated here
- If there are no errors, then terraform will return everything the script will create
  
Command- 'terraform apply'
- If there are no errors, terraform will run the script
  
Command- 'terraform destroy'
- This command will destroy everything created by terraform. Do NOT forget to destroy unused instances or it will be expensive.

**Any other instructions needed to setup configuration**
