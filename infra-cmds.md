# Git

Working Directory -> Staging Area (Stage) -> Local Repository -> Remote

*Set up for the first time only*
```bash
git config --global user.name <user_name>
git config --global user.email email@mail.com
git config --global color.ui auto
git config --list
(Optional)
git config --global core.editor code
```

🧩 *Simplified Git Guide (Basic to Advanced)*

🔹 1. Basic – Daily use

👉 The essentials for starting projects, making commits, and viewing status.
```bash
git help / git help --all / git help <command> → General help
git init → Initialize repo
git status → View status of changes
git add . → Add all changes
git add <path/file> → Add specific file
git commit -m "message" → Create commit
git commit -am "message" → Add changes and commit in one step
git log → Commit history
git log --oneline → Summary history
git show → View details of a commit
git diff → View differences without committing
git diff --staged / --cached → View differences from what has already been added
git restore --staged . → Remove files from staging
git mv file.txt new_name.txt → Rename file
git rm --cached file.txt → Delete file from Git control (but not from disk)
```

🔹 2. Intermediate – Teamwork, branches and stashes

👉 Here you start collaborating and managing branches.

🔸 Branches
```bash
git branch → View branches
git branch -a → View all (local + remote)
git branch <new_branch> → Create branch
git checkout <branch> → Change branch
git checkout -b <new_branch> → Create and change to the new
git switch <branch> → Modern alternative to checkout
git switch -c <new-branch-name> → Create a new branch
git switch --detach <commit_hash> → Switch to a specific commit 
git switch - → Undo the previous step
git branch -m <old_branch> <new_branch> → Rename branch
git branch -M main → Force change of name to main
git branch -D <branch> → Delete local branch
```

🔸 Stash (save changes without commit)
```bash
git stash → Save pending changes
git stash save "message" → Save with description
git stash list → View saved stashes
git stash apply <id> → Apply a stash without deleting it
git stash pop → Apply and delete stash
git stash drop stash@{n} → Delete a specific stash
```

🔸 Remote
```bash
git remote -v → View remote repos
git remote add origin <url> → Link remote
git remote add origin git@github.com:username/reponame.git
git remote remove <name> → Delete remote
git remote set-url origin <new_url> → Switch from HTTPS to SSH
```

🔸 Clone
```bash
git clone <url> → Clone repo
git fetch origin → Bring changes from the remote
```

🔹 3. Advanced – Synchronization, merges, rebases

👉 Here you already manage conflicts and synchronization between branches.

🔸 Pull / Push
```bash
git pull origin <branch> → Fetch and merge changes
git pull --rebase origin <branch> → Rebase while pulling
git pull -f origin <branch> → Force update
git push origin <branch> → Upload changes
git push -uf origin main → Force initial push
git push origin --delete <remote_branch> → Delete remote branch
git push -uf --all → Force push of all branches
```

🔸 Merge / Rebase
```bash
git merge <branch> → Merge changes
git config pull.rebase false  # merge
git config pull.rebase true → Use default rebase
git config pull.ff only       # fast-forward only
```

🔸 Tags
```bash
git tag → View tags
git tag -a v1.0 -m "message" → Create annotated tag
```

🔹 4. Very Advanced – Undo / Recovery / Cleanup

👉 Powerful commands, dangerous if not used carefully ⚠️

🔸 Revert changes
```bash
git commit --amend -m "new message" → Change message of the last commit
git commit --amend --no-edit → Add changes to the latest commit
git revert <commit> → Create a commit that reverts another
git revert <c1> <c2> → Revert multiple commits
```

🔸 Reset
```bash
git reset --soft <commit> → Delete commit but keep changes
git reset HEAD <file> → Remove file from staging
git reset --hard <commit> → ⚠️ Discard everything and revert to a commit
git reset --hard origin/master → Force remote state
```

🔸 Clean (untracked files)
```bash
git clean -n → Show what would be deleted
git clean -f → Delete untracked files
git clean -fd → Delete untracked files + folders
git clean -fdx → ⚠️ Delete ALL unversioned (including ignored)
```

🔹 5. Expert – Diagnosis and audit

👉 Useful commands for understanding history and solving problems.
```bash
git log --oneline --graph --decorate → Display branches graphically
git log --oneline --graph --all --decorate --abbrev-commit --pretty=full --pretty=format:"%h %s %d" --since="2021-01-01" --until="2021-01-31"
git log --pretty=format:"%h %s %d" → Custom log
git diff <hash1> <hash2> → Compare two commits
git diff <file> → Changes to a file
git reflog → View all history (including deleted commits)
```

# GitHub

gh-cli
```bash
gh --help
gh auth login --web
gh auth refresh -h github.com -s delete_repo
gh repo list
gh repo create --private username/repo-name # --public
gh repo edit --visibility public --accept-visibility-change-consequences username/repo-name
gh repo clone master username/repo-name
gh repo delete username/repo-name
```

(Just in case)

Docu

- https://docs.github.com/es/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys
- https://docs.github.com/es/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-&-adding-it-to-the-ssh-agent


SSH Keys
```bash
ssh-keygen -t ed25519
ssh-keygen -t RSA -C "email@mail.com"
```

----

# 🐳 Docker + Compose + ☸️ Kubernetes + HELM – Simplified command guide

🔹 1. Basic – Daily use

👉 The minimum to lift, view and stop containers/pods.

docker
```bash
docker --version, docker info → Version and environment info
docker search nginx
docker create --name container1 nginx
docker images -a / docker ps -a → List running images/containers
docker network / volume ls
docker ps -a → View all containers (even stopped ones)
docker pull <image> → Download image
docker run -d -p 8080:8080 <image> → Run container in background
docker stop app && docker rm app
docker stop <id|name> / docker rm <id|name> → Stop and delete container
docker logs -f <id|name> → View logs
```

Docker Compose
```bash
docker compose up -d → Start background services
docker compose up --build -d  # Rebuild + lift
docker compose down -v → Turn off services
docker compose logs -f        # Logs
docker compose ps -a → View containers lifted by Compose
```

Kubernetes (kubectl)
```bash
kubectl version / kubectl cluster-info → Version and cluster info
kubectl get pods / kubectl get all → View resources
kubectl describe pod <name> → Details of a pod
kubectl logs -f <pod> → Pod logs
kubectl exec -it <pod> -- bash → Enter a pod
```

🔹 2. Intermediate – Teamwork and deployments

👉 Here you start managing configurations, networks, services and volumes.

Docker
```bash
docker build -t <name>:<tag> -f Dockerfile . → Build image
docker exec -it <container> bash → Accessing an already running container
docker cp <origin> <container>:/path → Copy files to container
docker volume ls / docker network ls → View volumes / networks
docker network create <red> → Create network
```

Docker Compose
```bash
docker compose up --build -d → Rebuild and restore services
docker compose down -v → Power off and erase volumes
docker login / logout → Authentication on Docker Hub
docker push <repo/image> → Upload image to a registry
```

Kubernetes
```bash
kubectl apply -f file.yaml → Create/Update Resources from YAML
kubectl delete -f file.yaml → Delete resources
kubectl expose pod <pod> --type=LoadBalancer --port=80 → Expose service
kubectl expose deployment app --type=LoadBalancer --port=80 → Expose service
kubectl port-forward <pod> 9999:80 → Forward local ports ↔ pod
kubectl create deployment <name> --image=<image> → Create deployment
kubectl scale deployment <name> --replicas=3 → Scaling replicas
```

🔹 3. Advanced – Management, configuration and troubleshooting

👉 You already work with clusters, jobs, configmaps, secrets, & CI/CD.

Docker
```bash
docker inspect <image|container> → Advanced details
docker image prune -a / docker system prune -a --volumes → Clean space
docker commit <container> <new_image> → Create image from container
docker tag <image> <user>/<repo>:tag → Tag image
```

Docker Compose
```bash
docker compose -f override.yaml up -d → Use another Compose file
docker scout cves <image_id> → Vulnerability scanning
```

Kubernetes

Logs & debug
```bash
kubectl logs <pod> -c <container> → Logs of a specific container
kubectl top pods / kubectl top nodes → CPU/Memory Usage
```

ConfigMaps & Secrets
```bash    
kubectl create configmap <name> --from-file=<file>
kubectl create secret generic <name> --from-literal=key=value
```

Rollouts & updates
```bash
kubectl rollout status deployment <name>
kubectl rollout restart deployment app
kubectl rollout undo deployment <name>
```

Jobs & CronJobs
```bash
kubectl create job <name> --image=<image>
kubectl create cronjob <name> --image=<image> --schedule="* * * * *"
```

🔹 4. Expert – Advanced Production & Administration

👉 Here you enter the true DevOps level with monitoring, scaling, & security.

Docker

```bash
docker rm -f $(docker ps -aq) → Delete all containers
docker rmi -f $(docker images -q) → Delete all images
docker network rm $(docker network ls -q) → Delete all networks
docker volume rm $(docker volume ls -q)    # Delete volumes
docker system prune -a --volumes           # Full cleaning
```

Kubernetes

Advanced Objects/Items
```bash
kubectl get statefulset <name>
kubectl get daemonset <name>
kubectl get ingress
```

Cluster nodes
```bash
kubectl drain <node> → Remove node from the cluster
kubectl cordon <node> → Mark node as unschedulable
kubectl uncordon <node> → Reschedule pods on that node
```

Network policies
```bash
kubectl get networkpolicy
kubectl describe networkpolicy <name>
```

Audit
```bash
kubectl get <resource> -o yaml → View full definition
kubectl label pod <name> key=value → Tag resources
kubectl get pods -l key=value → Filter by label
```

# ☸️ Minikube — from basic to advanced

Basic (boot, status, IP, dashboard)

Start with Docker driver & a profile:
```bash
minikube start --driver=docker -p minikube
minikube start --driver=docker -p devCluster --nodes=2
```

View status / version / logs:
```bash
minikube status
minikube version
minikube logs
```

Cluster IP (per profile) & dashboard:
```bash
minikube ip -p minikube
minikube dashboard --port 30000
```

Stop/delete:
```bash
minikube stop
minikube delete -p minikube
```

Profiles & resources (CPU/RAM) ✅

List & select profile:
```bash
minikube profile list
minikube profile minikube
```

Adjust resources by profile:
```bash
minikube config set cpus 12 -p minikube
minikube config get cpus -p minikube
minikube config set memory 12G -p minikube
minikube config get memory -p minikube
```

Multi-node & runtimes

Multi-node cluster (Docker driver):
```bash
minikube start --driver=docker -p devCluster --nodes=2
```

Change runtime (e.g. CRI-O):
```bash
minikube start --container-runtime=cri-o -p cluster2
```

Force API server port:
```bash
minikube start --port=8443 --apiserver-port=8443 --driver=docker
```

Networks & service exposure

Get a direct URL to a Service:
```bash
minikube service <svc-name> --url -n <ns>
```

LoadBalancer locally (creates routes to LB type services):
```bash
minikube tunnel
```

Port-forward (kubectl, in case you don't want tunnel):
```bash
kubectl port-forward deploy/<name> 8080:80
```

Images: build, upload, & use within Minikube

Use the Docker daemon “inside” Minikube (so that Docker build makes the image available to the cluster):
```bash
eval $(minikube -p minikube docker-env)
docker build -t myapp:dev .
kubectl set image deploy/myapp myapp=myapp:dev
```

Alternative if you build off-site: upload local image to the cluster
```bash
minikube image load myapp:dev -p minikube
```

Access & troubleshooting

Shell inside the Minikube VM:
```bash
minikube ssh
```

Minikube logs (useful if the API server doesn't start):
```bash
minikube logs
```

k9s to explore the cluster (very comfortable):
```bash
k9s help
k9s info
```

Suggested flow (copy/paste)

A. Create profile with resources & two nodes
```bash
minikube profile minikube
minikube config set cpus 12 -p minikube
minikube config set memory 12G -p minikube
minikube start --driver=docker -p minikube --nodes=2
```

B. Rapid Deploy + Expose
```bash
kubectl create deploy web --image=nginx
kubectl expose deploy web --type=LoadBalancer --port=80
minikube tunnel   # o: minikube service web --url
```

C. Build local & update deployment
```bash
eval $(minikube -p minikube docker-env)
docker build -t web:dev .
kubectl set image deploy/web web=web:dev
```

D. Diagnosis
```bash
kubectl get pods -o wide
kubectl describe deploy/web
kubectl logs -f deploy/web
minikube logs
```

----

# ☸️ Kubernetes — Troubleshooting Commands

🔹 1. Check general condition
```bash
kubectl get all -o wide                # View all resources in more detail
kubectl get pods -n kube-system        # Review system pods
kubectl get nodes -o wide              # View node status
kubectl describe node <node>           # Details of a node
```

🔹 2. Review pods & containers
```bash
kubectl describe pod <pod>             # Events, errors, image used
kubectl get pod <pod> -o yaml          # Full YAML of the pod
kubectl logs <pod>                     # Logs of a container
kubectl logs -f <pod> --tail=100       # Streaming logs (last 100 lines)
kubectl logs <pod> -c <container>      # Logs of a specific container
kubectl exec -it <pod> -- bash         # Enter a pod
kubectl exec <pod> -- env              # View pod environment variables
```

🔹 3. Network & connectivity
```bash
kubectl get svc -o wide                # Check services & ports
kubectl describe svc <service>         # Service details
kubectl port-forward <pod> 8080:80     # Forward port to test local
kubectl run tmp --rm -it --image=curlimages/curl -- curl http://<svc>:<port>
```

🔹 4. Scaling & deployments
```bash
kubectl rollout status deployment <deploy>   # View deployment progress
kubectl rollout history deployment <deploy>  # Changelog
kubectl rollout undo deployment <deploy>     # Revert deployment
kubectl get rs -o wide                       # View active ReplicaSets
```

🔹 5. Resources & consumption
```bash
kubectl top pods               # Pod CPU/Memory Usage
kubectl top nodes              # Node CPU/Memory Usage
```

🔹 6. Cleaning & rapid testing
```bash
kubectl delete pod <pod> --grace-period=0 --force   # Force delete
kubectl get events --sort-by=.metadata.creationTimestamp   # View ordered events
kubectl run busybox --rm -it --image=busybox sh     # Temporary pod for debugging
```

----

# ⛵ Helm — Most used commands

🔹 1. Basic (daily use)
```bash
helm version                     # View Helm version
helm help                        # ?
helm repo list                   # View configured repos
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update                 # Update chart indexes
helm search repo nginx           # Search chart in local repos
helm search hub mysql            # Search chart in Artifact Hub
```

🔹 2. Install & manage releases
```bash
helm create my-chart
helm package ./my-chart
helm dependency update ./my-chart
helm install myapp bitnami/nginx         # Install a chart
helm install mydb bitnami/mysql -f values.yaml   # With custom values
helm list -A                             # List releases in all namespaces
helm status myapp                        # Status of a release
helm get all myapp                       # View details (templates + values)
helm get values myapp -n prod
helm get manifest myapp -n prod
```

🔹 3. Upgrade & rollback
```bash
helm upgrade myapp bitnami/nginx -f values.yaml   # Update release
helm upgrade --install myapp bitnami/nginx        # Install if not present (idempotent)
helm rollback myapp 1                             # Return to revision 1
helm history myapp                                # View upgrade history
helm history myapp -n prod                        # View upgrade history from prod namespace
helm rollback myapp 2 -n prod    # Return to version 2
```

🔹 4. Uninstallation & cleaning
```bash
helm uninstall myapp                 # Delete release
helm uninstall myapp --keep-history  # Delete but keep history
helm uninstall myapp -n prod         # Delete prod namespace
```

🔹 5. Working with values
```bash
helm show values bitnami/nginx > values.yaml   # Get default values
helm upgrade myapp bitnami/nginx --set replicaCount=3   # Passing values ​​inline
helm diff upgrade myapp bitnami/nginx -f values.yaml    # (if you have diff plugin) view differences before applying
```

🔹 6. Development & debugging
```bash
helm template myapp ./chart             # Render templates in YAML (without applying)
helm lint ./chart                       # Validate chart
helm dependency update ./chart          # Update chart dependencies
helm pull bitnami/nginx --untar         # Download chart & unzip
helm install --dry-run --debug myapp ./chart -f values-prod.yaml
```

----

# 🚀 Helm & Kubectl Troubleshooting Cheat Sheet (Production)

This document summarizes the **most commonly used commands** for diagnosing & troubleshooting production issues with **kubectl** & **helm**.

---

## 🔹 Kubectl (Troubleshooting en Kubernetes)

### 🔍 General inspection
```bash
kubectl get pods -A                      
kubectl get pods -n <namespace>          
kubectl describe pod <pod> -n <namespace>  
kubectl get events --sort-by=.metadata.creationTimestamp -A
```

### 📦 Logs
```bash
kubectl logs <pod> -n <namespace>                
kubectl logs <pod> -c <container> -n <namespace> 
kubectl logs -f <pod> -n <namespace>             
```

### 🚑 Debugging
```bash
kubectl exec -it <pod> -n <namespace> -- /bin/sh   
kubectl top pods -n <namespace>                   
kubectl top nodes                                 
kubectl get endpoints -n <namespace>              
```

### 🌐 Networks / Services
```bash
kubectl get svc -n <namespace>                    
kubectl describe svc <service> -n <namespace>     
kubectl get ingress -n <namespace>                
kubectl describe ingress <ingress> -n <namespace> 
```

---

## 🔹 Helm (Charts & Releases Troubleshooting)

### 📌 Release status
```bash
helm list -A                                  
helm status <release> -n <namespace>          
helm get values <release> -n <namespace>      
helm get manifest <release> -n <namespace>    
helm get hooks <release> -n <namespace>       
```

### 🛠️ Debugging of installation/upgrade
```bash
helm install <release> <chart> --dry-run --debug   
helm upgrade <release> <chart> --dry-run --debug   
helm template <chart> --values values.yaml         
```

### ⚡ Rollbacks
```bash
helm history <release> -n <namespace>              
helm rollback <release> <revision> -n <namespace>  
```

---

## 🔹 Typical troubleshooting flow in production

1. `kubectl get pods -n <ns>` → view pod status
2. `kubectl describe pod <pod> -n <ns>` → review events
3. `kubectl logs <pod> -n <ns>` → look at errors in container
4. `kubectl get svc,ingress -n <ns>` → validate exposure/network
5. `helm status <release> -n <ns>` → view release status
6. `helm get values <release> -n <ns>` → confirm configuration
7. `helm template ... --debug` → validate manifests
8. If nothing works → `helm rollback <release> <rev>`  

---

# Terraform

🌍 Terraform — Simplified Commands (from basic to advanced)

🔹 1. Basic – Daily Use (Basic IaC)

👉 To initialize, validate, plan, apply & destroy.
```bash
terraform -v / terraform -help → Version & help
terraform init → Initialize the directory
terraform validate → Validates file syntax
terraform fmt / terraform fmt -recursive → Format files
```
Plan, Apply, Destroy
```bash
terraform plan                # Sample plan
terraform plan -out=planfile  # Save plan to file
terraform apply -auto-approve # Apply changes
terraform apply planfile      # Apply a saved plan
terraform destroy -auto-approve   # Destroy everything
terraform destroy -target=resource  # Destroys only one resource
```

🔹 2. Intermediate – Variables, Outputs, Workspaces

👉 Environment management & configuration.

Variables
```bash
export TF_VAR_name="value"         # Define environment variable
terraform plan -var="key=value"    # Define variable in CLI
terraform plan -var-file="dev.tfvars"  # Use variables file
```
Outputs
```bash
terraform output   # Show outputs
```
Workspaces (environments)
```bash
terraform workspace new dev
terraform workspace list
terraform workspace select qa
terraform workspace delete qa
```

🔹 3. Advanced – State & Providers

👉 Advanced health & infrastructure management.

State
```bash
terraform state list                # List of resources
terraform state show <resource>     # Resource details
terraform state mv old new          # Move resource in the state
terraform state rm <resource>       # Delete resource from the state
terraform refresh                   # Refresh real state vs tfstate
```
Providers & Graph
```bash
terraform providers   # Tree of providers used
terraform graph | dot -Tpng > graph.png  # Visualize dependencies
```
🔹 4. Expert – Corrections & special cases

👉 For advanced scenarios & production issues.

Replacement of resources
```bash
terraform apply -replace=<resource>  # modern method
terraform taint <resource>        # (deprecated) brand to recreate
terraform untaint <resource>      # removes the taint
```
Import existing resources
```bash
terraform import aws_instance.myec2 i-0a1b2c3d4e5f6g7h8
```
Remote state
```bash
terraform state pull  # Download remote state
terraform state push  # Upload remote state
```
Locking
```bash
terraform force-unlock <LOCK_ID>   # Releasing a blocked state
```
Terraform Cloud
```bash
terraform login    # Save credentials
terraform logout   # Delete credentials
```

🔹 5. Practical laboratory (example of flow through environments)

👉 Lab 1 - Example.
```bash
# Create workspace for Dev
terraform workspace new dev
terraform plan -var-file="env/dev.tfvars" -out=dev.plan
terraform apply -auto-approve dev.plan
```
```bash
# Create workspace for QA
terraform workspace new qa
terraform plan -var-file="env/qa.tfvars" -out=qa.plan
terraform apply -auto-approve qa.plan
```
```bash
# Switch between envs
terraform workspace select dev
terraform workspace select qa
```
```bash
# Destroy envs
terraform destroy -auto-approve -var-file="env/dev.tfvars"
terraform destroy -auto-approve -var-file="env/qa.tfvars"
```

----

# Vagrant (Just in case)

```bash
vagrant plugin install vagrant-vmware-desktop
vagrant up --provider=vmware_desktop
vagrant ssh
vagrant reload --provision
vagrant suspend
vagrant halt
vagrant destroy
vagrant box list
vagrant box remove bento/ubuntu-24.04
vagrant status
vagrant ssh-config
```
---

<- [CLI-GUI](cli-gui.md)

<- [VSC-EXTENSIONS](vsc-ext.md)

<- [README](README.md)