# steps to install docker on ubuntu server

Docker installation on Ubuntu Server involves several straightforward steps using the official Docker repository method, which ensures you get the latest stable version with security updates.

### Prerequisites

Update the system and install required dependencies:

```bash
sudo apt update
sudo apt upgrade -y
sudo apt install apt-transport-https ca-certificates curl software-properties-common gnupg lsb-release
```

These packages enable APT to use repositories over HTTPS and provide necessary tools for the installation process.[^2][^3]

### Add Docker's Official Repository

Add Docker's GPG key to verify package authenticity:

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

Add the Docker repository to your APT sources:

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Update the package index to include the new repository:

```bash
sudo apt update
```

This ensures you're installing Docker from the official repository rather than Ubuntu's default repositories.[^4][^5]

### Install Docker Engine

Install Docker Community Edition and its components:

```bash
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

This command installs Docker Engine, CLI tools, container runtime, and Docker Compose plugin.[^1][^2]

### Start and Enable Docker Service

The Docker service starts automatically after installation, but you can verify and enable it:

```bash
sudo systemctl status docker
sudo systemctl enable docker
sudo systemctl start docker
```


### Verify Installation

Test Docker by running the hello-world container:

```bash
sudo docker run hello-world
```

This downloads a test image and runs it in a container, confirming successful installation.[^4][^1]

### Optional: Add User to Docker Group

To run Docker commands without sudo, add your user to the docker group:

```bash
sudo usermod -aG docker $USER
```

Log out and back in for changes to take effect, then test with:

```bash
docker run hello-world
```


### Check Docker Version

Verify the installed version:

```bash
docker --version
docker-compose --version
```

This method installs the latest stable Docker version with all necessary components for container management and orchestration.
<span style="display:none">[^10][^11][^12][^13][^14][^15][^16][^17][^18][^19][^20][^6][^7][^8][^9]</span>

