🚀 From Zero to Production in 10 Days

Hands-on AWS Project: High Availability, Security, and Regional Failover
▶ Watch the full walkthrough videoBuilt and deployed a multi-region, production-grade AWS architecture in just 10 days. (https://lnkd.in/ehg8hwRE)

📘 Project Overview
This was my first 10 days of hands-on AWS experience, built immediately after earning my AWS Solutions Architect – Associate certification. The project was designed to simulate real-world conditions: disaster recovery, high availability, automated scaling, secure backend access, and global DNS-based failover. While the work happened across 10 build sessions, the dates are not strictly sequential — I progressed as time allowed, including during a bout of pneumonia. I’ve since added day-by-day documentation to reflect each major architectural change, aligning with best practices around CI/CD pipeline documentation.

What This Project Demonstrates
-------------------------------
✅ Multi-AZ EC2 instances with Auto Scaling
🔁 Cross-zone load balancing using Application Load Balancer (ALB)
🔒 Private/public subnet isolation via NAT Gateway☁️ S3 static site failover, CloudFront global acceleration, and WAF edge protection
🌎 Latency-based regional routing with Amazon Route 53
🧱 Infrastructure as Code with CloudFormation (fully region-portable template)

📍 Deployed Regions
-------------------
- us-east-1 (Northern Virginia)
- us-west-1 (Northern California)

🛠️ Key Skills Demonstrated
---------------------------
- Designing for high availability, disaster recovery, and auto healing
- Implementing security best practices using NAT, private subnets, and AWS WAF
- Building regionally redundant architectures
- Translating hands-on learning into Infrastructure as Code
- Hosting public DNS with Route 53 and validating failover logic
- Documenting infrastructure changes in GitHub (CI/CD pipeline alignment)

📆 Architecture Milestones Timeline
====================================
Date      Milestone
----------------------------------------------------------
03/27/25  Initial EC2 and ALB deployed in us-east-1
03/29/25  NAT Gateway and private backend instance added
04/02/25  AMI used to deploy second region (us-west-1)
04/04/25  CloudFormation template created to replicate architecture
04/06/25  Replaced CloudFront with Route 53 latency-based routing
(See BUILD_LOG.md for full details on all ten sessions.)

📂 Repository Contents
-----------------------
template.yaml — CloudFormation template (region-portable)
BUILD_LOG.md — Day-by-day implementation log
README.md — You’re here!
Walkthrough video — linked above

🙋‍♂️ About Me
===============
I’m a certified AWS Solutions Architect who built this as my first hands-on AWS project — and I’m now looking for my Day 1 on a professional cloud team. Let’s connect!

linkedin.com/in/robert-caruso-aws
GitHub: github.com/Bob-OCPLinkedIn:
-----------------------------------
