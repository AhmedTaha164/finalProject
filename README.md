# Weather-App
This Weather App is a DevOps project that integrates continuous integration, containerization, and infrastructure automation. It provides real-time weather information for various locations and is built using Python, JavaScript, HTML, and CSS. The application utilizes the OpenWeatherMap API to fetch current weather data.

![image](https://github.com/user-attachments/assets/1a48fe84-6461-41c7-b3c0-50950f0cfee9)

## Prerequisites
- Two Linux virtual machines
- Docker installed on both virtual machines
- Jenkins installed and configured to push to your GitHub repository
- Ansible installed

## Steps to Deploy

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/AhmedTaha164/finalProject.git
   cd finalProject
   ```

2. **Insert Your VM Private Keys**:
   - Place your virtual machine private keys inside the `finalProject/ansible/` directory.

3. **Modify the Inventory File**:
   - Update the `inventory` file to include your virtual machines' IP addresses.

4. **Run Vagrant**:
   ```bash
   vagrant up
   ```
   - This will provision the virtual machines and set up the environment.

5. **Confirm Inventory Configuration**:
   ```bash
   ansible -i inventory all -m ping
   ```
   - This ensures Ansible can communicate with the virtual machines.

6. **Configure Jenkins for GitHub Integration**:
   - Add an SSH key to Jenkins so it can push to your GitHub repository.

7. **Configure Jenkins for DockerHub Integration**:
   - Grant Jenkins the necessary permissions to push images to your DockerHub repository.

8. **Modify Ansible Playbook**:
   - Update the Ansible playbook to push the application image to your DockerHub repository.

9. **Run the Jenkins Pipeline**:
   - Execute the Jenkinsfile to automate the build and deployment process.
10- You can access website by typing 192.168.56.10:5000 or 192.168.56.9:5000

## Screenshots
### VM1
![image](https://github.com/user-attachments/assets/3a8f8360-60f1-467d-bc8b-c9ec01353c35)


### VM2
![image](https://github.com/user-attachments/assets/f7bb595c-55b3-46d6-aac8-068f94d3737b)




