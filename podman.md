### Section #1 - What is Podman
Podman is a daemonless, open source, Linux native tool designed to make it easy to find, run, build, share and deploy applications using Open Containers Initiative (OCI) Containers and Container Images. Podman provides a command line interface (CLI) familiar to anyone who has used the Docker Container Engine. Most users can simply alias Docker to Podman (alias docker=podman) without any problems. Similar to other common Container Engines (Docker, CRI-O, containerd), Podman relies on an OCI compliant Container Runtime (runc, crun, runv, etc) to interface with the operating system and create the running containers. This makes the running containers created by Podman nearly indistinguishable from those created by any other common container engine.

### Section #2 - Installing Podman on Windows
1. Download the Podman Windows installer
![01](img/img1.jpg)
After this point, podman.exe will be present on your PATH, and you will be able to run the podman machine init command to create your first machine.

#### Step 2.1 - Machine Init Process
1. After WSL is installed, the init command will install a minimal installation of Fedora, customizing it to run podman.
```
PS C:\Users\Riyan> podman machine init
Extracting compressed file
Importing operating system into WSL (this may take 5+ minutes on a new WSL install)...
Installing packages (this will take a while)...
Complete!
Configuring system...
Generating public/private ed25519 key pair.
Your identification has been saved in podman-machine-default
Your public key has been saved in podman-machine-default.pub
The key fingerprint is:
SHA256:RGTGg2Q/LX7ijN+mzu8+BzcS3cEWP6Hir6pYllJtceA root@WINPC
Machine init complete
To start your machine run:

        podman machine start
```

#### Step 2.2 - Starting Machine
1. After the machine init process completes, it can then be started and stopped as desired:
```
PS C:\Users\User> podman machine start

Starting machine "podman-machine-default"

This machine is currently configured in rootless mode. If your containers
require root permissions (e.g. ports < 1024), or if you run into compatibility
issues with non-podman clients, you can switch using the following command:

        podman machine set --rootful

API forwarding listening on: npipe:////./pipe/docker_engine

Docker API clients default to this address. You do not need to set DOCKER_HOST.
Machine "podman-machine-default" started successfully
```

#### Step 2.3 - First Podman Command
1. From this point on, podman commands operate similarly to how they would on
Linux. 
For a quick working example with a small image, you can run the Linux date
command on PowerShell.
```
PS C:\Users\Riyan> podman run ubi8-micro date
Thu May 5 21:56:42 UTC 2022
```

#### Step 2.4 - Listing Podman Machine(s)
1. To list the available podman machine instances and their current resource
usage, use the `podman machine ls` command:
```
PS C:\Users\Riyan> podman machine ls


NAME                    VM TYPE     CREATED      LAST UP            CPUS        MEMORY      DISK SIZE
podman-test-riyan  wsl         1 hours ago  Currently running  4           200.1MB     570MB
```

