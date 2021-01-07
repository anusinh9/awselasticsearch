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
    $ git clone https://github.com/anusinh9/awselasticsearch.git

For the sake for simplicty if you are not using AWS CLI, you can use the the access key and secret access key provided by AMAZON as environment variables to prevent it from using hard-coded secrets. Find below examples (these secrets are dummy and wont work in real life)

    $ export AWS_ACCESS_KEY_ID="your access key"
    $ export AWS_SECRET_ACCESS_KEY="your secret key"
    $ export AWS_DEFAULT_REGION="ap-south-1"  #ap-south-1 (Mumbai region has been selected to avoid the latency)


💡 Pro Tip : If you have AWS CLI configured locally, Terraform can use that configuration too for authentication with AWS which is more robust as we have options of selection of different profiles for authentication.
# from version 0.11 and later interpolation can be ignored we can also use "AWS_ACCESS_KEY_ID" but for versions compatibility we will stick with it as during terraform plan it will throw only warnings but no errors.

🚀 Execution Once the above code has been dowloaded first setup the remote backend infrastructur using terraform

    $ terraform init
    $ terraform apply -auto-approve


# Question and Answers
1. What did you choose to automate the provisioning and bootstrapping of the instance? Why?
💡 Automation provides and abstraction layer where a well written code can be re-used and re-deployed again and which can avoid the possibilty of human error.
2. How did you choose to secure ElasticSearch? Why?
💡 By providing
1- node-2-node encryption
2 - encryption for data at rest (not bundled with AWS free tier)
3. How would you monitor this instance? What metrics would you monitor?
💡 By Providing Cloudwatch log groups and setting up different alarms based on cloudwatch
4. Could you extend your solution to launch a secure cluster of ElasticSearch nodes? What
would need to change to support this use case?
💡 Indeed We can use fine -grained access control to restrict the access further for the cluster setup and also we can setup master nodes which are handy when it comes to manage cluster in a more secure manner.
5. Could you extend your solution to replace a running ElasticSearch instance with little or no
downtime? How?
💡 Yes Indeed we can used the "snapshot_options" where we can store snaphots depending upon hours and when required we can bring up cluster using snapshot in no time.
6. Was it a priority to make your code well structured, extensible, and reusable?
💡 Yes indeed using  IAC we are making sure code is re-usable and extensible as our priority.
7. What sacrifices did you make due to time?
💡 Not much I had to balance my professional commitments, it took around 1 day of some study and 1 day for implementation and testing.
