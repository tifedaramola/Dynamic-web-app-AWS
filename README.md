![Alt text](3._Host_a_Dynamic_Web_App_on_AWS.png)

---

# Hosting a Dynamic Web Application on AWS  

## Project Overview  

This project demonstrates the deployment of a dynamic web application on AWS using an EC2 instance while ensuring scalability, security, and high availability. The deployment utilizes AWS services such as VPC, ALB, Auto Scaling, RDS, S3, and IAM for a secure and efficient cloud-hosted application.  

The architecture is designed to follow best practices in cloud infrastructure management, including network segmentation, load balancing, secure data storage, and automated scaling.   

## Resources Used  

1. **Virtual Private Cloud (VPC)**  
   - Configured with both public and private subnets across two availability zones to enable network segmentation for security and high availability.  

2. **Internet Gateway**  
   - Provides internet connectivity for resources in the public subnet, including the ALB and NAT Gateway.  

3. **NAT Gateway**  
   - Deployed in the public subnet to allow private EC2 instances to access the internet securely (e.g., for software updates) while preventing inbound internet access.  

4. **Multiple Availability Zones**  
   - Ensures fault tolerance and high availability by distributing resources across two availability zones.  

5. **Application Load Balancer (ALB)**  
   - Deployed in the public subnets to distribute incoming traffic evenly across multiple web servers in private subnets, improving availability and fault tolerance.  

6. **Private Subnets**  
   - Hosts private resources such as web servers and RDS database instances, ensuring security by restricting direct internet access.  

7. **Security Groups**  
   - Acts as a virtual firewall to control inbound and outbound traffic for EC2 instances, ALB, and databases, enforcing strict security policies.  

8. **EC2 Instance Connect Endpoint**  
   - Provides a secure connection to EC2 instances in private subnets without requiring an internet-exposed bastion host.  

9. **Auto Scaling Groups**  
   - Manages EC2 instances in private subnets to ensure high availability, scalability, and elasticity by automatically adjusting the number of instances based on traffic demand.  

10. **Amazon S3**  
   - Used to store project web files, ensuring secure and scalable file storage.  

11. **IAM Role**  
   - Grants EC2 instances permissions to securely access S3 buckets, enhancing security by avoiding the use of static credentials.  

12. **AWS Certificate Manager (ACM)**  
   - Manages SSL/TLS certificates to secure application communications, ensuring encrypted data transmission.  

13. **Amazon Machine Image (AMI) & Launch Template**  
   - AMI stores pre-configured EC2 instance settings, while the launch template automates instance provisioning for consistency and efficiency.  

14. **Amazon Route 53**  
   - Used for domain name registration and DNS routing to map custom domain names to the ALB for seamless user access.  

## Deployment Scripts  

Deployment scripts for setting up and hosting the application are available in the repository. These scripts automate the configuration and deployment process, ensuring an efficient and repeatable setup.  

For detailed scripts and implementation, visit the [GitHub Repository](https://github.com/tifedaramola/Dynamic-web-app-AWS.git).  

## Summary of Errors Encountered  

During the deployment process, the following issues were encountered:  

- **Error establishing connection with the database** – RSA Public Key Error.  
- **Flyway command syntax error** – Incorrect command usage during database migration.  

## Troubleshooting and Resolution  

The following steps were taken to resolve the errors:  

1. **Database Connection Issue:**  
   - Adjusted the Flyway connection string to include the following parameters:  
     ```
     useSSL=false&allowPublicKeyRetrieval=true
     ```
   - This resolved the RSA Public Key error and established a secure connection with the database.  

2. **Flyway Command Syntax Issue:**  
   - Corrected the Flyway command syntax to align with best practices and proper SQL migration execution.  

3. **Path and Environment Variable Configuration:**  
   - Verified and correctly set environment variables to ensure the database migration tool could locate the necessary files.  

4. **Migration Outcome:**  
   - Despite initial warnings, the migration was ultimately successful, and the system is now correctly configured for future database migrations.  

## Conclusion  

This project successfully demonstrates how to deploy a secure, scalable, and highly available dynamic web application on AWS using best practices. The troubleshooting process further reinforced the importance of precise configuration, debugging, and environment management when deploying cloud-based applications.  

---


