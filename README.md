# 🚀 DevOps Bot CLI

DevOps Bot CLI is a unified tool for automating cloud provisioning, CI/CD pipelines, configuration management, and more. It supports a **YAML-driven** architecture to streamline operations across AWS and remote infrastructure with **zero friction**.

---

## 🧰 Available Commands

```bash
dob --help
```

| Command        | Description                                             |
|----------------|---------------------------------------------------------|
| `dob aws`      | Manage AWS cloud infrastructure                         |
| `dob infracycle` | Execute build & deployment pipelines                  |

---

## 🛠️ Installation

### Debian/Ubuntu:
```bash
sudo dpkg -i devops-bot_0.1_amd64.deb
```

### RHEL/CentOS:
```bash
sudo rpm -i devops-bot-0.1-1.x86_64.rpm
```

### macOS:
```bash
chmod +x dob-macos
sudo mv dob-macos /usr/local/bin/dob
dob --help
```

### Windows:
```powershell
dob.exe --help
```

---

## ⚙️ Post-Installation Setup

### 1. Configure AWS Credentials:
```bash
dob aws config \
  --access_key <AWS_ACCESS_KEY> \
  --secret_key <AWS_SECRET_KEY> \
  --region us-east-1
```

### 2. Verify CLI access:
```bash
dob aws --help
dob infracycle --help
```

---

## ☁️ AWS Provisioning Example

Use the `aws screenplay` command to launch infrastructure:

```bash
dob aws screenplay path/to/provision.yaml 
```

### Sample AWS Screenplay Template (`provision.yaml`):

```yaml
resources:
  vpcs:
    - name: MyVPC
      cidr_block: 10.0.0.0/16
      region: us-east-1
      tags:
        - Key: Name
          Value: MyVPC

  subnets:
    - cidr_block: 10.0.1.0/24
      availability_zone: us-east-1a
      vpc_id: ${vpc_id}
      auto_assign_public_ip: true
      region: us-east-1
      tags:
        - Key: Name
          Value: MySubnet

  ec2_instances:
    - name: Runner
      instance_type: t2.small
      ami_id: ami-05088768490
      key_name: devops-bot
      subnet_id: ${subnet_id}
      region: us-east-1
      security_group: ${security_group_id}
      count: 1
      tags:
        - Key: Name
          Value: Runner
```

---

## 🔁 Infracycle CI/CD Example

Run a full pipeline using:

```bash
dob infracycle apply --file-path path/to/pipeline.yaml 
```

### Sample Infracycle Pipeline Template:

```yaml
mode: remote
identifier: Runner
category: prod
username: root

jobs:
  - name: sample-job
    stages:
      - name: Clone Repo
        tasks:
          checkout:
            enabled: true
            provider: github
            source_url: https://github.com/your/repo.git
            clone_dir: /tmp/devops_bot

      - name: Install Dependencies
        tasks:
          sh:
            enabled: true
            steps:
              - "apt-get update -y"
              - "apt-get install -y nodejs npm"

      - name: Build Project
        tasks:
          npm:
            enabled: true
            working_directory: /tmp/devops_bot
            steps:
              install: true
              build: true

      - name: Archive Build
        tasks:
          archive_artifact:
            enabled: true
            artifact_dir: /tmp/devops_bot
            artifact_name: my-node-app
            archive_format: tar.gz

      - name: Upload to Azure
        tasks:
          upload_artifact:
            enabled: true
            target: blob_storage
            archive_path: /tmp/devops_bot/my-node-app.tar.gz
            container_url: "https://...blob.core.windows.net/container?sp=..."
```

---

## 🧪 Supported Targets for `upload_artifact`

| Target         | Upload Method        |
|----------------|----------------------|
| `s3`           | AWS S3 Buckets       |
| `blob_storage` | Azure Blob Storage   |
| `gcp`          | Google Cloud Storage |
| `jfrog`        | JFrog Artifactory    |
| `nexus`        | Sonatype Nexus       |
| `github`       | GitHub Packages      |
| `gitlab`       | GitLab Package Registry |

---

## 📩 Contact

For enterprise inquiries or feedback, contact us at:

📧 **info@devops-bot.com**  
🌐 [devops-bot.com](https://devops-bot.com)

---

## 🏷️ Release Info

**Version**: `0.1`  
**Release Name**: `test2`  
**Commit Hash**: `25ce770`

