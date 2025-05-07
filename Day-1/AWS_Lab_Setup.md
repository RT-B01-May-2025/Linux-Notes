# AWS Lab Setup

## 1. Create an AWS Account
- Sign up at: [AWS Signup Link](https://signin.aws.amazon.com/signup?request_type=register)

- Reference Doc: [AWS Setup Guide](https://docs.google.com/document/d/1Mt8aaR8A8oNvutPVPf9ksik5V8LhHX9Q/edit#heading=h.xsn31xvaqv0q)

## 2. Log in to Your AWS Account
- Use your registered credentials to access [AWS Console](https://aws.amazon.com/console/).

## 3. Launch an EC2 Instance
1. Go to **EC2 Dashboard** → **Launch Instance**.
2. Choose an **AMI (Amazon Machine Image)** (e.g., Amazon Linux, Ubuntu).
3. Select an instance type (**t2.micro** for free-tier users).
4. Configure networking (default settings work for now).
5. **Download the key pair (.pem file)** for SSH access.
6. Launch the instance.

## 4. Connect to the EC2 Instance
Use any of the following SSH tools:

### **SSH Tools (Windows & Mac)**
| Tool | Download Link |
|------|--------------|
| **GitBash (Windows)** | [Download](https://git-scm.com/downloads) |
| **Putty** | [Download](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html) |
| **Super Putty** | [Download](https://github.com/jimradford/superputty) |
| **MobXterm** | [Download](https://mobaxterm.mobatek.net/download.html) |
| **Mac Terminal** | Pre-installed |

### **SSH Connection Command**
For GitBash or Mac Terminal:
```bash
ssh -i "your-key.pem" ec2-user@your-ec2-public-ip

