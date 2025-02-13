# Ansible Playbook for Rancher Setup

## Overview
This Ansible playbook automates the installation and setup of Rancher on an Ubuntu server. It performs the following steps:

1. Updates and upgrades Ubuntu packages.
2. Installs OpenSSH Server.
3. Installs cURL and verifies the version.
4. Installs Docker (compatible with Rancher).
5. Adds the user to the Docker group.
6. Pulls the Rancher Docker image.
7. Runs the Rancher container with the required settings.
8. Retrieves the Rancher container ID.
9. Extracts the Rancher bootstrap password.
10. Displays the Rancher access URL.

## Prerequisites
- Ansible installed on your control node.
- Target server running Ubuntu.
- User with sudo privileges.
- Docker must not be pre-installed (if already installed, ensure it's compatible with Rancher).

## Installation
1. Clone this repository or copy the playbook files to your Ansible directory.
   ```sh
   git clone <repository_url>
   cd <repository_directory>
   ```

2. Define your target server(s) in an inventory file (`inventory.ini`):
   ```ini
   [rancher_host]
   192.168.138.146 ansible_user=your_user
   ```

## Usage
1. Run the Ansible playbook with:
   ```sh
   ansible-playbook -i inventory.ini setup_rancher.yml
   ```

2. Wait for the setup to complete.

3. Once finished, open your browser and go to:
   ```
   http://192.168.138.146
   ```

4. Retrieve the Rancher bootstrap password from the output logs.

## Troubleshooting
- Ensure Ansible is installed with:
  ```sh
  ansible --version
  ```
- Verify SSH connectivity to the target server:
  ```sh
  ssh your_user@192.168.138.146
  ```
- Check if Docker is installed:
  ```sh
  docker --version
  ```
- If the Rancher container is not running:
  ```sh
  docker ps -a
  ```
  Restart it if necessary:
  ```sh
  docker start rancher
  ```

## License
This project is licensed under the MIT License.

## Author
[Your Name]
