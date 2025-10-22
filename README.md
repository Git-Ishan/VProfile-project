# VProfile Project

**VProfile** is a multi-tier web application stack. It is a social networking site developed in Java.

## Objectives
- Learn VM automation locally
- Set up a real-world project locally (so that R&D can be done freely)

## Tools
- **Hypervisor:** Oracle VM VirtualBox
- **Automation:** Vagrant
- **CLI:** Git Bash
- **IDE:** Sublime Text

## Architecture Overview
The first user accesses the application via the IP address of a load balancer. We use Nginx to simulate a load balancer, which routes requests to Apache Tomcat (the Java web application server).

If the application requires external storage, we use NFS servers (shared storage). The application resides in Tomcat, where the user receives the login page. Login credentials are stored in a MySQL database.

Additionally, there is a RabbitMQ service connected to Tomcat. In this project, it is primarily for added complexity—it acts as a message broker (a queuing agent connecting applications). SQL queries from the login process are sent to the MySQL server. After the first attempt, login information is cached using Memcached.

## Getting Started
1. Clone the repository and ensure it is set to local rather than main.  
2. Perform manual provisioning first, followed by the automated version.  
3. Bring up all VMs one by one using:
   ```bash
   vagrant up
4. SSH into each VM and install the necessary services for the project.  

After setup, validate that **Nginx**, **Tomcat**, the **Application**, and the **Database** are working correctly.

## Problems with Manual Provisioning
- Difficult to make changes on real servers
- Local setup is complex
- Time-consuming
- Not repeatable

## Benefits of Automated Setup
- Fully automated
- Repeatable
- Infrastructure as Code (IaC)
- Allows R&D on your own machine

Above, we performed all steps manually: SSH-ing into each VM and entering commands. Using scripts, we can automate this entire process, running it with a single command. **Vagrant handles all the heavy lifting**, and we just wait for the setup to complete.


Project setup and stacks

<img width="1016" height="616" alt="Vprofile project setup" src="https://github.com/user-attachments/assets/2952974d-2cf1-428c-b01e-9acb2e5470f3" />

Login page

<img width="1120" height="616" alt="login" src="https://github.com/user-attachments/assets/bdcce629-324f-42f0-a619-ff286c514954" />

<img width="1120" height="664" alt="welcome" src="https://github.com/user-attachments/assets/872d2512-7485-4981-b47a-b9fffae65210" />

Memcache is working

<img width="1095" height="590" alt="memcache is working" src="https://github.com/user-attachments/assets/e8bb0ad4-f813-4584-8887-a948153dfb6c" />

Rabbitmq is working 

<img width="943" height="482" alt="rabbitmq is working" src="https://github.com/user-attachments/assets/29c5688f-8f9a-4981-8f57-d3ee5fe27eda" />
