# awselasticsearch
⚡️ #This repo is all about spinning your own aws elasticsearch service using IAC Terraform.

👨‍💻 Preparation

1 - Installing terraform binary before we start up

One can directly get the latest terraform binar from " https://releases.hashicorp.com/terraform/0.14.3 " based on the release version or directly you can login to your local unix machine (which we have used in this setup) and follow below steps:

    $ cd ~ $ wget https://releases.hashicorp.com/terraform/0.14.3/terraform_0.14.3_linux_amd64.zip 
    $ unzip terraform_0.14.3_linux_amd64.zip (this is will unzip the binary package downloaded from above step) 
    $ sudo cp terraform /usr/bin/terraform (this is will allow terraform binary to be placed in your users current path) you can check if terraform binary has been placed successfully via below 2 commands

    $ which terraform
    $ terraform --version

First of all, download the source code 
    $ git clone https://github.com/anusinh9/test_scalereal.git
    $ cd test_scalereal

For the sake for simplicty if you are not using AWS CLI, you can use the the access key and secret access key provided by AMAZON as environment variables to prevent it from using hard-coded secrets. Find below examples (these secrets are dummy and wont work in real life)

    $ export AWS_ACCESS_KEY_ID="your access key"
    $ export AWS_SECRET_ACCESS_KEY="your secret key"
    $ export AWS_DEFAULT_REGION="ap-south-1"  #ap-south-1 (Mumbai region has been selected to avoid the latency)


💡 Pro Tip : If you have AWS CLI configured locally, Terraform can use that configuration too for authentication with AWS which is more robust as we have options of selection of different profiles for authentication.
# from version 0.11 and later interpolation can be ignored we can also use "AWS_ACCESS_KEY_ID" but for versions compatibility we will stick with it as during terraform plan it will throw only warnings but no errors.

🚀 Execution Once the above code has been dowloaded first setup the remote backend infrastructur using terraform

    $ terraform init
    $ terraform apply -auto-approve
