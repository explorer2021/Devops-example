# Create a First Maven Jenkins job to build hello-world project 
# *Jenkins Job name:* `First_Project_Maven_Hello_World`

We know how to use work with each and Git, Jenkins independently. What if you want to collaborate these two? that is where Simple DevOps project helps you. Follow the below steps if you are a new guy to DevOps. You love it. 


#### Pre-requisites

1. Jenkins server 


### Steps to create "First_Project_Maven_Hello_World" Jenkin job
1. Login to Jenkins console
1. Create *Jenkins job*, Fill the following details,
   - *Source Code Management:*
      - Repository: `https://github.com/explorer2021/hello-world`
      - Branches to build : `*/master`  
   - *Build:*
     - Root POM:`pom.xml`
     - Goals and options: `clean install package`
   - *Output/After Deployment:*
      ```sh
      [root@jenkins target]# pwd
      /var/lib/jenkins/workspace/First_Maven_Project_Hello_World/webapp/target
      [root@jenkins target]# ls -ltr *.war
      -rw-r--r-- 1 jenkins jenkins 2527 Oct 28 10:13 webapp.war
      ```
