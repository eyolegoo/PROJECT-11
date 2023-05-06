# PROJECT-11
Ansible configuration management – automate project 7 to 10


## Ansible configuration management – automate project 7 to 10

## ***INSTALL AND CONFIGURE ANSIBLE ON EC2 INSTANCE***

1. - Update Name tag on your Jenkins EC2 Instance to Jenkins-Ansible. We will use this server to run playbooks.

2. - In your GitHub account create a new repository and name it **ansible-config-mgt**.

3. - Install **Ansible**

```
sudo apt update

sudo apt install ansible
```

- Check your Ansible version by running ansible --version

<img width="643" alt="Ansible and python version" src="https://user-images.githubusercontent.com/115954100/236633947-0573b1de-d685-44e1-a67f-41e956f863b4.png">

4. - Configure Jenkins build job to save your repository content every time you change it – this will solidify your Jenkins configuration skills acquired in [Project 9](https://www.darey.io/docs/tooling-website-deployment-automation-with-continuous-integration-introduction-to-jenkins/)

- Create a new Freestyle project ***ansible*** in Jenkins and point it to your ‘ansible-config-mgt’ repository.

- Configure Webhook in GitHub and set webhook to trigger ***ansible*** build.

- Configure a Post-build job to save all (**) files, like you did it in Project 9.

5. - Test your setup by making some change in README.MD file in master branch and make sure that builds starts automatically and Jenkins saves the files (build artifacts) in following folder

`ls /var/lib/jenkins/jobs/ansible/builds/<build_number>/archive/`

- **Note**: Trigger Jenkins project execution only for /main (master) branch.

- Now your setup will look like this:

<img width="571" alt="Architecture topology" src="https://user-images.githubusercontent.com/115954100/236634374-635c611c-1ce4-4648-afe8-edc9d650d569.png">

- **Tip** Every time you stop/start your Jenkins-Ansible server – you have to reconfigure GitHub webhook to a new IP address, in order to avoid it, it makes sense to allocate an [Elastic IP](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html) to your Jenkins-Ansible server (you have done it before to your LB server in ***Project 10***). Note that Elastic IP is free only when it is being allocated to an EC2 Instance, so do not forget to release Elastic IP once you terminate your EC2 Instance.

## ***Step 2 – Prepare your development environment using Visual Studio Code***

1. - First part of ‘DevOps’ is ‘Dev’, which means you will require to write some codes and you shall have proper tools that will make your coding and debugging comfortable – you need an [Integrated development environment (IDE) or Source-code Editor](https://en.wikipedia.org/wiki/Integrated_development_environment). There is a plethora of different IDEs and Source-code Editors for different languages with their own advantages and drawbacks, you can choose whichever you are comfortable with, but we recommend one free and universal editor that will fully satisfy your needs – [Visual Studio Code (VSC)](https://en.wikipedia.org/wiki/Visual_Studio_Code), you can get it [here](https://code.visualstudio.com/download).

2. - After you have successfully installed VSC, ***configure it to connect to your newly created GitHub repository***.

3. - Clone down your ansible-config-mgt repo to your Jenkins-Ansible instance

`git clone <ansible-config-mgt repo link>`
