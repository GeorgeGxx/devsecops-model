## Terminal

`Install`

- Powershell 7.4.x `Windows Store`
- Terminal `Windows Store`
  - Settings -> Startup -> Default profile -> PowerShell
- Warp Terminal 
  - https://www.warp.dev


`Chocolatey` (PWSH > Run as Administrator just for Install)

- https://chocolatey.org/install

```bash
##### Use example: #####
choco list
choco search <package_name>
choco upgrade -y <package_name>
choco uninstall -y <package_name>
choco install -y peazip

- <package_name>
  - awscli

choco install -y awscli awssamcli azure-cli gh git glab gradle graphviz javadecompiler-gui k9s kubernetes-cli kubernetes-helm kubernetes-helmfile kubernetes-kops liberica11jdk liberica17jdk liberica21jdk liberica8jdk maven Minikube nvm opentofu python311 serverless sqlitestudio terraform vault

choco install -y go --version=1.24.6

choco upgrade -y peazip
```

`Google Cloud CLI` - GCLOUDSDK (gcloud)

- https://cloud.google.com/sdk/docs/install

## Pip (Install with Powershell > Run as Administrator)

### Checkov (PaC for IaC) - CICD Available in GitHub Marketplace

`Use example`
```bash
pip install checkov    
pip install -U checkov
checkov -d . //<folder_path/project_name>
```

### Boto 3 (AWS SDK for Python)

```bash
pip install boto3
```

### Google Cloud Compute (SDK)

```bash
pip install google-cloud-compute
```

## WSL2 Ubuntu
```bash
wsl -s Ubuntu ### (Set default WSL distro to Ubuntu)

sudo apt install -y zip unzip curl
```

`For Quarkus`

SDKMAN
- https://sdkman.io/install
```bash
sdk list java
sdk install java 17.0.9-graalce 21.0.2-graalce 21.0.8-librca 17.0.16-librca
sdk uninstall java < Identifier >
sdk use java 21.0.8-librca
sdk default java < Identifier >
sdk current java
```
Source-to-image (S2I)

- https://computingforgeeks.com/install-source-to-image-toolkit-on-linux/

## Variables

`Java ... Maven ... Gradle ...`

> Sys
```bash
JAVA_HOME: C:\Program Files\BellSoft\LibericaJDK-21
MAVEN_HOME: C:\ProgramData\chocolatey\lib\maven\apache-maven-3.9.11
GRADLE_HOME: C:\ProgramData\chocolatey\lib\gradle\tools\gradle-9.0.0
CLOUDSDK_PYTHON: C:\Python311\python.exe
```
> Path
```bash
%JAVA_HOME%\bin
C:\Program Files\BellSoft\LibericaJDK-17\bin
C:\Program Files\BellSoft\LibericaJDK-11\bin 
C:\Program Files\BellSoft\LibericaJDK-8\bin
%MAVEN_HOME%\bin
%GRADLE_HOME%\bin
C:\Program Files\MongoDB\Server\7.0\bin
C:\Users\jorge\AppData\Local\Programs\mongosh
C:\Program Files\PostgreSQL\16\bin
C:\Program Files\MySQL\MySQL Server 8.4\bin
%CLOUDSDK_PYTHON%
```

## Browsers
  
  - Chrome
    - https://chromeenterprise.google/download

## Productivity

  - Freda `Windows Store`
  - Adobe reader 
    - https://get.adobe.com/reader
  - Microsoft Office 
    - https://www.office.com
  
## Collab
  
  - WhatsApp `Windows Store`
  - Microsoft Teams 
    - https://www.microsoft.com/en-us/microsoft-teams/download-app
  - Zoom 
    - https://zoom.us/download

## Architecture

  - Draw.io 
    - https://www.draw.io
  - Bizagi Modeler 
    - https://www.bizagi.com/en/platform/modeler

## IDEs
  
  - VSCode 
    - https://code.visualstudio.com
  - IntelliJ `Community`
    - https://www.jetbrains.com/idea/download
  - Postman 
    - https://www.postman.com
  - Dbeaver `Community`
    - https://dbeaver.io

## DataBase

  - SSMS
    - https://aka.ms/ssmsfullsetup
  - MongoDB Community 6.x.x + Compass + Mongosh 
    - https://www.mongodb.com/try/download/community 
    - https://www.mongodb.com/try/download/shell
  - MySQL 8.x.x `LTS` 
    - https://dev.mysql.com/downloads/mysql
  - PostgreSQL 16.x
    - https://www.postgresql.org/download
  
## Dockerization
  
  - Docker desktop + WSL Ubuntu `Windows Store` + DockerHub Registry 
    - https://www.docker.com/products/docker-desktop 
    - https://hub.docker.com
    - https://docs.docker.com/scout
---

-> [VSC-EXTENSIONS](vsc-ext.md)

-> [INFRA-COMMANDS](infra-cmds.md)

<- [README](README.md)

