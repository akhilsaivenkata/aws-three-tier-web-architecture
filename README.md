# AWS Three Tier Web Architecture Workshop

## Description
This project is a hands-on implementation of a three-tier web architecture in AWS, utilizing application code provided by the AWS workshop. Throughout this process, I manually built the necessary components and configurations to deploy this architecture in an available and scalable manner.

## Audience
This is intended for individuals with a technical role. The assumption is that you have at least some foundational AWS knowledge around VPC, EC2, RDS, S3, ELB, and the AWS Console.

## Pre-requisites
1. An AWS account. If you don’t have an AWS account, follow the instructions [here](https://aws.amazon.com/console/) and click on the “Create an AWS Account” button in the top right corner.
2. An IDE or text editor of your choice.

## Architecture Overview
![Architecture Diagram](https://github.com/aws-samples/aws-three-tier-web-architecture-workshop/blob/main/application-code/web-tier/src/assets/3TierArch.png)

In this architecture, a public-facing Application Load Balancer forwards client traffic to our web tier EC2 instances. The web tier runs Nginx web servers configured to serve a React.js website and redirects API calls to the application tier’s internal-facing load balancer. The internal-facing load balancer then forwards that traffic to the application tier, which is written in Node.js. The application tier manipulates data in an Aurora MySQL multi-AZ database and returns it to our web tier. Load balancing, health checks, and autoscaling groups are created at each layer to maintain the availability of this architecture.

## Key Steps and Components Created

1. **S3 Bucket Creation**:
   - Created an S3 bucket to store the code for the entire application.

2. **IAM Role Creation**:
   - Created an IAM role to attach to the EC2 instances for secure access to AWS resources.

3. **VPC and Subnets**:
   - Created a new VPC and established 6 subnets (2 public and 4 private) across two Availability Zones in a region.

4. **Internet Gateway**:
   - Created an Internet Gateway to allow external access to the public subnets.

5. **Security Groups**:
   - Configured multiple security groups for different tiers, including:
     - App tier
     - Web tier
     - Internet-facing Application Load Balancer (ALB)
     - Internal Application Load Balancer (ALB)
     - Database security group

6. **Aurora/MySQL Database**:
   - Provisioned an Aurora MySQL database with a read replica in another Availability Zone for fault tolerance.

7. **EC2 Instances**:
   - Launched 2 EC2 instances and configured the web tier and app tier applications. Created AMIs from these instances for scalability and deployment.

8. **Load Balancing and Auto Scaling**:
   - Created target groups using the AMIs, set up ALBs, and configured Auto Scaling groups for both the app tier and web tier instances.

9. **Component Connectivity**:
   - Connected all components during configuration to ensure proper communication and functionality.

10. **Resource Management**:
    - Ensured that all components were terminated or deleted post-deployment to avoid unnecessary billing.

## Learnings
- Gained hands-on experience in designing and deploying a three-tier architecture in AWS.
- Improved understanding of various AWS services and their integration.
- Learned best practices for resource management and cost optimization in AWS.

## Screenshots and Recordings
- ![Deployment Screenshot](path/to/your/screenshot.png)
- ![Application Screenshot](path/to/your/screenshot2.png)
- [Video Recording of the Final Application](link-to-your-video)

## Conclusion
This project significantly enhanced my understanding of AWS and its services. I look forward to exploring more advanced features and optimizations in future projects.

## Security
See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License
This library is licensed under the MIT-0 License. See the LICENSE file.
