# 🛠️ AWS Project – Build Log (10-Day Architecture Breakdown)

This file contains a detailed breakdown of what was implemented during each of the ten build sessions. While this was my first hands-on AWS project, the architecture evolved rapidly and was built with high availability, regional failover, and production-grade patterns in mind.

---

## Day 1 – 03/21/25  
**Initial Setup & Public Web Server**
- Created a new AWS environment in us-east-1
- Created IAM admin user with MFA and access keys
- Deleted root access key per best practices
- Installed AWS CLI and verified access
- Created initial security group with inbound rules for SSH (22) and HTTP (80)
- Launched EC2 instance in `us-east-1c` and installed Apache
- Verified access to Apache welcome page via public IP

---

## Day 2 – 03/26/25  
**Domain Setup & S3 Static Site Failover**
- Purchased `bobssandbox.com` via Route 53
- Created a public hosted zone and A record for EC2 IP
- Configured S3 bucket for static website hosting with index.html and error.html
- Built and uploaded basic static HTML content to S3
- Created health check and failover routing in Route 53 between EC2 and S3

---

## Day 3 – 03/27/25  
**Redundancy via Cross-Zone Load Balancing**
- Created AMI from original EC2 instance
- Deployed new EC2 instance in `us-east-1b` using AMI
- Verified Apache was pre-installed and configured
- Created Application Load Balancer (ALB) across `us-east-1b` and `1c`
- Attached both EC2 instances to the ALB target group
- Verified ALB served content from both AZs

---

## Day 4 – 03/29/25  
**Auto Scaling & Notifications**
- Configured Auto Scaling Group (ASG) across `us-east-1b` and `1c`
- Attached launch configuration using the same AMI
- Defined scaling policies based on CPU utilization
- Created SNS topic and subscription for scaling event email alerts
- Verified ASG and ALB integration with scaling in/out triggers

---

## Day 5 – 03/30/25  
**Private Subnet & Backend Simulation**
- Created private subnet in `us-east-1b` with /24 CIDR block
- Deployed EC2 backend instance without public IP
- Created NAT Gateway in public subnet for outbound internet access
- Created and configured jump box in public subnet for secure access to backend instance
- Verified backend EC2 could reach internet and receive updates

---

## Day 6 – 04/01/25  
**CloudFront Distribution Integration**
- Created CloudFront distribution with ALB as origin
- Configured origin behaviors and caching policies
- Restricted direct ALB access using CloudFront headers
- Updated DNS to route traffic through CloudFront
- Verified global accessibility and performance boost

---

## Day 7 – 04/02/25  
**Web Application Firewall (WAF) Integration**
- Created AWS WAF Web ACL
- Attached WAF to CloudFront distribution
- Configured default rules (IP match, rate limiting)
- Verified WAF blocked unwanted traffic and allowed legitimate requests

---

## Day 8 – 04/04/25  
**Infrastructure as Code with CloudFormation**
- Used Former2 to export live infrastructure to CloudFormation YAML
- Edited YAML for region independence using !Ref, !GetAtt, and Parameters
- Validated and tested template with stack preview
- Created documentation inline in template for clarity

---

## Day 9 – 04/05/25  
**Region Replication (West Coast Build)**
- Deployed CloudFormation stack to us-west-1 (California)
- Verified full infrastructure replicated: VPCs, subnets, ALBs, EC2, NAT, ASG, etc.
- Confirmed working failover and backend communication
- Updated DNS to reflect new ALB endpoints

---

## Day 10 – 04/07/25  
**Route 53 Latency-Based Routing**
- Removed CloudFront distribution from DNS configuration
- Created two A records in Route 53: one for each regional ALB
- Configured latency-based routing policy using us-east-1 and us-west-1
- Verified DNS resolution and traffic routing matched region proximity
- Simulated failover by taking down one region’s ALB
- Removed S3 static failover website

