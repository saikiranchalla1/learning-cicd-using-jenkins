# Introduction to Continuous Integration
![process-before-ci](imgs/process-before-ci.png)

Drawbacks of the process:
- No constant feedback
  - Developers have to wait till the application is deployed and the QA team verifies it
- Bug fixing - Costly
  - Locating and fixing the bugs by itself becomes a time consuming process
- Slow software delivery
  - software delivery process became slow and inconsistent with a lot of "ifs" and "buts"

![afterci](imgs/afterci.png)

![benefits of ci](imgs/benefits-of-ci.png)

![what is ci](imgs/what-is-ci.png)

![CICD](imgs/cicd.png)

![Continuous Delivery vs Deployment](imgs/cotntinuous-delivery-vs-deployment.png)

![Benefits of Continuous Integration](imgs/benefits-of-continuous-integration.png)

![CI Principles and Practices](imgs/ci-principles-and-practices.png)


# Introduction to Jenkins
![what is jenkins](imgs/what-is-jenkins.png)

![CICD with Jenkins](imgs/cicd-with-jenkins.png)

![Features of Jenkins](imgs/features-of-jenkins.png)

![distributed-architecture](imgs/distributed-architecture.png)

![Jenkins Pipeline](imgs/jenkins-pipeline.png)


# Installation of Jenkins
- The process to install Jenkins is similar irrespective of the operating system you are using.
![step by step process](imgs/step-by-step-process.png)

- Download JDK for your operating system from [here](https://www.oracle.com/java/technologies/downloads/#java11-windows).

- Follow the Installation process for your platform as described [here](https://docs.oracle.com/en/java/javase/11/install/overview-jdk-installation.html#GUID-8677A77F-231A-40F7-98B9-1FD0B48C346A).
- Next, let's download and install Jenkins.
- Navigate to Jenkins [download](https://www.jenkins.io/download/) page and download the required files for your operating system. __DOWNLOAD THE FILE FROM LTS LIST.__
- After installing Jenkins, it will open the Jenkins Ui in browser.
- Find the initial Jenkins password by following the instructions in the UI. For example:

![initial password](imgs/initial-password.png)

- Next, click on the `Install` button to install Jenkins and create the first admin user.


# Jenkins Dashboard and Configuration
![Jenkins Terms](imgs/jenkins-terms.png)

- Open Jenkins in your browser, by navigating to `http://localhost:8080`.
- The main page that you see is called the `Dashboard`.
- Here's a brief description of the various links you see on the UI:
  - New Item: This is used to create a new job or project.
  - People: configure who can use the Jenkins system and how they login along with their permissions.
  - Build History: A history of the builds that have run on this Jenkins instance.
  - Manage Jenkins: A single place to configure everything related to the Jenkins instance.
  - My Views: Custom views created by a user.
  - Credentials: Place to store secrets in Jenkins, for example a secret to login to Github can be stored here.
- Manage Jenkins is an interesting section, so let's dive further into this. Click on Manage Jenkins followed by `Configure System.`
  - On the Manage Jenkins page, you will see the following options:
  ![manage jenkins](imgs/manage-jenkins.png)
  - Click on the 'Configure System'.
  ![configure system](imgs/configure-system.png)
  - Home Directory: Jenkins requires some disk space to perform builds and keep archives. You can check this location from the configuration screen of Jenkins. By default, this is set to ~/.jenkins, and this location will be initially stored within your user profile (such as C:\Users\Nikita\.jenkins) location.

  ![home directory](imgs/home-directory.png)

  - You can change this location to a different location to store all relevant builds and archives. We can do this in the following ways:
    - Set environment variable of JENKINS_HOME to the new home directory before launching the servlet container.
    - Set system property of JENKINS_HOME to the servlet container.
    - Set JNDI (Java Naming and Directory Interface) environment entry JENKINS_HOME to the new directory.
  - Let's see to set the JENKINS_HOME environment variable.
  - First, create a new folder in any directory. And copy all the contents from the ~/.jenkins to a new folder.
  - Set the JENKINS_HOME environment variable to the newly created folder, which is also pointing to the base directory location where Java is installed on your machine.
  - Now, in the Jenkins dashboard, click on the Manage Jenkins from the left-hand side menu, and then click on the Configure System from the right-hand side.
  - In the Home directory option, you will now see the directory which has been configured.


  - System Message: Here you can enter a message that will be broadcast to all the users of the Jenkins users.
  - # of executors: number of parallel jobs that can be run at a given time.
  ![number of executors](imgs/number-of-executors.png)
  - Quiet Period: Number of seconds Jenkins should wait before starting a new job.
  - SCM checkout retry count: Number of times Jenkins should retry connection to SCM like Github.
  - Restrict project Naming: Allows us to define a pattern for naming jobs in Jenkins.
  - Environment Variables: This option is used to add custom environment variables which will apply to all the jobs. Environment variables are key-value pairs and can be accessed and used in Builds wherever required. (For example: SLACK_TOKEN, SAUCE_API_KEY ).

  ![environment variables](imgs/executors.png)

  - Jenkins URL: By default, the Jenkins URL is set to the localhost. If you have a DNS (domain name setup) for your machine, set this to the domain name else overwrite localhost with the IP of machine. This will help in setting up slaves (nodes) and while sending out links using the email as you can directly access the Jenkins URL using the environment variable JENKINS_URL which can be accessed as ${JENKINS_URL}.

  ![jenkins URL](imgs/jenkins-url.png)
We'll dive into the rest of the settings when we need them.

# Jenkins - Management
- To manage Jenkins, click on the "Manage Jenkins" option from the left hand of the Jenkins Dashboard page.

![manage jenkins02](imgs/manage-jenkins02.png)

- When you click on the Manage Jenkins, you will get the various options to manage the Jenkins:

![click on manage jenkins](imgs/click-on-manage-jenkins.png)

- We have a lot of options in Jenkins Management page like:

  - Configure System
  - Configure Global Security
  - Configure Credentials
  - Global Tool Configuration
  - Reload Configuration from Disk
  - Manage Plugins
  - System Information
  - System Log
  - Load Statistics
  - Jenkins CLI
  - Script Console
  - Manage Nodes
  - About Jenkins
  - Manage Old Data and
  - Prepare for Shutdown
- Configure System: In this, we can manage paths to the various tools to use in builds, such as the versions of Ant and Maven, as well as security options, email servers, and other system-wide configuration details. Jenkins will add the required configuration fields dynamically when new plugins are installed.


![configure-system-2](imgs/configure-system-2.png)

- Configure Global Security: Configure Global Security option provides the ability to set up users and their relevant permissions on the Jenkins instance. By default, you will not want everyone to be able to define builds or other administrative tasks in Jenkins. So Jenkins provides the ability to have a security configuration in place.

![configure global security-2](imgs/configure-global-security-2.png)

- Reload Configuration from Disk: Jenkins stores all its system and job configuration details as XML files and all XML files are stored in the Jenkins home directory. Jenkins also stores all of the build histories.

If you are moving build jobs from one Jenkins instance to another or archiving old build jobs, you will have to insert or remove the corresponding build job directories to Jenkins's builds directory. You do not have to take Jenkins offline to do this?you can simply use the "Reload Configuration from Disk" option to reload the Jenkins system and build job configurations directly.

- Manage Plugin: Here you can install a wide or different variety of third-party plugins from different Source code management tools such as Git, ClearCase or Mercurial, to code quality and code coverage metrics reporting. We can download, install, update, or remove the plugins from the Manage Plugins screen.

![manage plugins](imgs/manage-plugins.png)

- System Information: This option displays a list of all the current Java system properties and system environment variables. Here you can check what version of Java is currently running in, what user it is running under, and so forth.

![system properties](imgs/system-properties.png)

- System Log: The System Log option is used to view the Jenkins log files in real time. As well as, the main use of this option is for troubleshooting.

![system logs](imgs/system-logs.png)

- To see the logs click on the 'All Jenkins Logs'.

![logs](imgs/logs.png)

- Load Statistics
This option is used to see the graphical data on how busy the Jenkins instance is in terms of the number of concurrent builds and the length of the build queue which provides an idea of how long your builds need to wait before being executed. These statistics can show you a good idea of whether extra capacity or extra build nodes are required from an infrastructure perspective.

![stats](imgs/stats.png)

- Jenkins CLI
Using this option, you can access various features in Jenkins through a command-line. To run the Jenkins through cli, first you have to download the Jenkins-cli.jar file and run it on your command prompt as follows:

java -jar jenkins-cli.jar -s http://localhost:8080/jenkins/

This page gives the list of available commands with their description.

![jenkins-cli](imgs/jenkins-cli.png)

- Script Console
This option allows you to run Groovy scripts on the server. This option is very useful for advanced troubleshooting since it requires a strong knowledge of the internal Jenkins architecture.

![script console](imgs/script-console.png)

- Manage nodes
Jenkins can handle parallel and distributed builds. In this page, you can configure how many builds you want. Jenkins runs concurrently, and, if you are using distributed builds, set up builds nodes. A build node (slave) is another machine that Jenkins can use to execute its builds.

![manage nodes](imgs/manage-nodes.png)

- About Jenkins
This option will show the version and license information of the Jenkins you are running. As well as it displays the list of all third party libraries.


![about jenkins](imgs/about-jenkins.png)

- Prepare for Shutdown
If you want to shut down Jenkins, or the server Jenkins is running on, it is best not to do so when a build is being executed. To shut down Jenkins cleanly, you can use the Prepare for Shutdown link, which prevents any new builds from being started. Eventually, when all of the current builds have completed, you will be able to shut down Jenkins cleanly.

![prepare for shutdown](imgs/prepare-for-shutdown.png)


# Creating Users and Granting Access in Jenkins
Generally, in a large organization, there are multiple separate teams to run and manage jobs in Jenkins. But managing this crowd of users and assigning roles to them is too difficult.

By default, when you create a user in Jenkins, it can access almost everything. In this, you can create multiple users but can only assign the same global roles and privileges to them. This is not ideal, especially for large organizations.

To enable you to assign different roles and privileges to different users in Jenkins, you should have to install the Role Strategy Plugin.

## Install Role-based Authorization Strategy Plugin
- Step 1: Open your Jenkins dashboard by visiting http://localhost:8080/jenkins

- Steps 2: Click on 'Manage Jenkins' and select the 'Available' tab.
![plugin manager](imgs/plugin-manager.png)

- Step 3: On the filter option, type "role-based" and press Enter.
![role based authorization](imgs/role-based-authorization.png)

- Step 4: Now, select the plugin and click on 'Install without restart' button.
![restart Jenkins](imgs/restart-jenkins.png)

## Enable Role-Based Strategy on Jenkins
- Step 1: After Plugin installation, go to the 'Manage Jenkins' and then click on 'Configure Global Security'.
![configure security](imgs/configure-security.png)


When you click the Configure Global Security option then you will see the following page:
![security page](imgs/security-page.png)

Check on Enable security option.

- Step 2: On the Security Realm section, select 'jenkins' own user database'.

  - On Authorization section, select 'Role-Based Strategy'.
![configure global security ](imgs/configure-global-security.png)

Click on Save.

- Step 3: You will be prompted to add your first user. Here, we are setting up an admin user for the system.
![first admin user](imgs/first-admin-user.png)

Click on Create First Admin User.

![first admin user created](imgs/first-admin-user-created.png)

## Creating User on Jenkins
- Step 1: Now it's time to setup your users in the system. When you go to manage Jenkins and scroll down, you will see the 'Manage Users' option. Click on this option.
![manage users](imgs/manage-users.png)

- Step 2: Just Like, you defined the admin user, and start creating other users for the system. Let's create another user:

To create another user click on 'Create User' option on the left hand side of the Manage Users page.
![create user](imgs/create-user.png)

![Create user next step](imgs/create-user-next-step.png)

Click on Create User button.

## Managing User Roles on Jenkins
- Step 1:

  - Click on Manage Jenkins.
  - Select Manage and Assign Roles. Note that, Manage and Assign Role will only be visible if you have installed the Role strategy plugin.
![manage and assign roles](imgs/manage-and-assign-roles.png)

- Step 2: Click on Manage Roles option to add new roles.
![manage and assign roles - 2](imgs/manage-and-assign-roles-2.png)

- Step 2: To create a new role called "developer".

  - Type "developer" in the Role to add option.
  - Click on Add to create a new role.
  - Now, select the appropriate permissions that you want to assign to the developer role.
  - Then Click on Save button.
![creating developer role](imgs/creating-developer-role.png)

## Assigning User Roles on Jenkins
- Step 1: Now, you have created roles, let's assign them to specific users.

  - Click on Manage Jenkins.
  - Then select Manage and Assign Roles.
  - Click on Assign Roles.
![assign roles UI](imgs/assign-roles-ui.png)

- Step 2: Let's add new role "developer" to user.

  - Add the User name on User/group to add option.
  - Click on Add button.
![add user to group](imgs/add-user-to-group.png)

- Select "developer" role check box.
![assign user to a role](imgs/assign-user-to-a-role.png)


- You can assign any role to any user as per your requirement.
- Then click on Save.
