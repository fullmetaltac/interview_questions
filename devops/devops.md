# Table of Contents
- [Table of Contents](#table-of-contents)
  - [Git](#git)
    - [git ref log](#git-ref-log)
    - [merge vs rebase](#merge-vs-rebase)
  - [Docker](#docker)
    - [Dockerfile Example](#dockerfile-example)
  - [Kubernetes](#kubernetes)
    - [Basic structure of a deployment.yaml file](#basic-structure-of-a-deploymentyaml-file)
  - [References](#references)

## Git

### git ref log

`git reflog` shows a log of all changes made to the tips of branches (like `HEAD`), including those that are no longer visible in `git log`.

It's like a safety net — you can recover lost commits, even after `reset`, `rebase`, or `checkout`.

```bash
git reflog
--------------------------------------------
a1b2c3d HEAD@{0}: reset: moving to HEAD~1
f4e5d6c HEAD@{1}: commit: Add login feature
```
You can restore a commit like this:
```bash
git checkout HEAD@{1}
```

**When to use**:

- You accidentally ran git reset --hard or lost commits after a rebase.
- You want to find an older state of your branch.


### merge vs rebase

- **git merge**:  

Combines two branches and keeps the full history.
Results in a merge commit. History stays branchy.
```bash
git checkout main
git merge feature-branch
```
Use merge when you want to preserve context and avoid rewriting history (e.g., in team environments).

- **git rebase**:  

Moves commits from one branch onto another, rewriting history.
Results in a linear history.

```bash
git checkout feature-branch
git rebase main
```

Use rebase when you want a clean, linear history, especially before pushing a feature branch.

## Docker

### Dockerfile Example

```Dockerfile
# Use an official Python base image
FROM python:3.11-slim

# Set the working directory inside the container
WORKDIR /app

# Copy the requirements file into the container
COPY requirements.txt .

# Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the application code
COPY . .

# Define the default command to run the app
CMD ["python", "app.py"]
```

How to use it

```bash
# Build the Docker image from the Dockerfile in the current directory
docker build -t my-python-app .                    # -t names the image "my-python-app"

# Run a container from the built image
docker run -d -p 5000:5000 my-python-app           # -d runs in background, -p maps port 5000 (host:container)

# List running containers to get the container ID or name
docker ps                                          # shows active containers

# Open an interactive shell in the running container
docker exec -it <container_id_or_name> /bin/bash   # useful for debugging or inspecting the container

```
## Kubernetes

### Basic structure of a deployment.yaml file

```yaml
apiVersion: apps/v1                # API version of the Deployment
kind: Deployment                   # Type of Kubernetes resource
metadata:
  name: my-app                     # Name of the deployment
  labels:
    app: my-app                    # Labels for selection and grouping
spec:
  replicas: 2                      # Number of pod replicas
  selector:
    matchLabels:
      app: my-app                  # Select pods with this label
  template:
    metadata:
      labels:
        app: my-app                # Label pods (must match selector)
    spec:
      containers:
        - name: my-container       # Name of the container
          image: nginx:1.21        # Docker image to use
          ports:
            - containerPort: 80    # Port the container exposes
```
How to use it

```bash
kubectl apply -f deployment.yaml   # Create or update
kubectl get deployments            # Verify deployment is created
kubectl get pods                   # See the running pods
kubectl delete -f deployment.yaml  # Delete deployment and its pods
```

## References
 - https://github.com/gracco/sysadmin-interview-questions/blob/master/README.md
    