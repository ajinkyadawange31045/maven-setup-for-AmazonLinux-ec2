# maven setup for Amazon Linux in ec2 instance
### To Install Apache Maven and Java 8 on your EC2 instance

1. Connect to your Amazon EC2 instance with an SSH client.
2. Install Apache Maven on your EC2 instance. First, enter the following to add a repository with a Maven package.
```bash
sudo wget https://repos.fedorapeople.org/repos/dchen/apache-maven/epel-apache-maven.repo -O /etc/yum.repos.d/epel-apache-maven.repo
```

Resource been used for the above setup is : https://docs.aws.amazon.com/neptune/latest/userguide/iam-auth-connect-prerq.html
