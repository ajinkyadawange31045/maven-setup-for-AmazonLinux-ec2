# maven setup for Amazon Linux in ec2 instance
### You should know how to create the instance in ec-2
Go to ec2, click on "Launch Instance", do the needful and launch instance.
You can watch some YouTube video for more guidance on ec2.

### To Install Apache Maven and Java 8 on your EC2 instance

1. Connect to your Amazon EC2 instance with an SSH client.
2. Install Apache Maven on your EC2 instance. First, enter the following to add a repository with a Maven package.
```bash
sudo wget https://repos.fedorapeople.org/repos/dchen/apache-maven/epel-apache-maven.repo -O /etc/yum.repos.d/epel-apache-maven.repo
```

Enter the following to set the version number for the packages.
```bash
sudo sed -i s/\$releasever/6/g /etc/yum.repos.d/epel-apache-maven.repo
```

Then you can use yum to install Maven.
```bash
sudo yum install -y apache-maven
```

The Gremlin libraries require Java 8. Enter the following to install Java 8 on your EC2 instance.
```bash
sudo yum install java-1.8.0-devel
```

Enter the following to set Java 8 as the default runtime on your EC2 instance.
When prompted, enter the number for Java 8.
```bash
sudo /usr/sbin/alternatives --config java
```

Enter the following to set Java 8 as the default compiler on your EC2 instance.
```bash
sudo /usr/sbin/alternatives --config javac
```

Now if you want to install a webapp, use the following command -
```bash
mvn archetype:generate -DgroupId=in.ajinkya -DartifactId=My-first-webapp -DarchetypeArtifactId=maven-archetype-webapp -DinteractiveMode=false
```

Now if you want to install a simple app, use the following command -
```bash
mvn archetype:generate -DgroupId=in.ajinkya -DartifactId=Ajinkya-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
```


Now you can run the following command, which are often called as mvn goals and check weather installation happened properly or not
```bash
mvn clean
mvn compile
mvn package
```

Resource been used for the above setup is : https://docs.aws.amazon.com/neptune/latest/userguide/iam-auth-connect-prerq.html
