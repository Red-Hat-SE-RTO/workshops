# Exercise 2.3 - Add Execution Environment for RHEL System Roles

## Table of Contents

* [Objective](#objective)
* [Step 1 - Run “LINUX / Setup Builder”](#step-1---run-linux--setup-builder)
* [Step 2 - Create custom Execution Environment with RHEL System Roles collection](#step-2---create-custom-ee-with-rhel-system-roles-collection)
    * [2.1 - Access Terminal](#21---access-terminal)
    * [2.2 - Tell builder where to look for collections](#22---tell-builder-where-to-look-for-collections)
    * [2.3 - Define how you want your EE built](#23---define-how-you-want-your-ee-built)
    * [2.4 - Add RHEL System Roles collection](#24---add-rhel-system-roles-collection)
    * [2.5 - Pull down base image](#25---pull-down-base-image)
    * [2.6 - Build EE](#26---build-ee)
    * [2.7 - Add EE to Automation Controller](#27---add-ee-to-automation-controller)

## Objective

In Exercise 3 from Section 1 of this workshop, you were able to do a deep dive into Ansible Builder.  But what happens after that?  You need to store your EE's where they can be shared and version controlled.  This time you will be creating your own custom EE in your personal workshop environment. From there you will push it to your very own Private Automation Hub.  Once you have your EE's in a container repository (such as PAH) you need to put it into production by adding it to your Automation Controller. 

### Step 1 - Run “LINUX / Setup Builder”

In exercise 2.2, the "LINUX / Setup Builder" job template was created.  Now we will execute this job template to build out an Ansible Builder environment on our controller node (**ansible-1** in **Workshop Inventory**). 

* Go to: **Resources** -> **Templates** -> launch **LINUX / Setup Builder**
    * Enter **“ansible-1”** for "**Server Name or Pattern"** in Survey
    * Click **Next**
    * Click **Launch**

### Step 2 - Create custom EE with RHEL System Roles collection

#### 2.1 - Access Terminal

* Access Terminal on **ansible-1** through VSCode:<br>
![vscode credentials](images/vscode_creds.png)
* Open "/home/student/" folder: <br>
![folder navigation](images/select_folder.png)
* Enter "/home/student/" and click ok<br>
![directory path](images/home_student_directory.png)
* Start a terminal sesesion:<br>
![start terminal](images/open_terminal.png)

#### 2.2 - Tell builder where to look for collections
The ansible configuration file located in the ee project directory appropriately named rhel_system_roles_ee, is where you define the sequence in which builder where search for collections when building the EE.
* Open the execution_environments/rhel_system_roles_ee/ansible.cfg file:<br>
![navigation to ansible.cfg](images/nav_to_ansible_config.png)
* Edit **server_list** to list search precidence for collections.  Update your file as follows:<br>
```ini
[galaxy]
server_list = automation_hub, galaxy
```
* Complete the **\[galaxy_server.automation_hub\]** **url**, **auth_url**, and **token** information:
    * **\[galaxy_server.automation_hub\]**: gathered from console.redhat.com (in [Section 2/Exercise 1/Step 1](../2.1-evnironment-prep/README.md) of this workshop)<br>
    <span style="color:red">(NOTE: again, don't load token again, it will invalidate the token we set up in Automation Controller)</span>
    * **\[galaxy_server.galaxy\]:** is already configured for you
    * Final ansible.cfg file looks like:<br>
    (NOTE: tokens and urls will be different):<br>
```ini
[galaxy]
server_list = automation_hub, private_automation_hub, galaxy
 
[galaxy_server.automation_hub]
url="https://console.redhat.com/api/automation-hub/content/#######-synclist/"
auth_url="https://sso.redhat.com/auth/realms/redhat-external/protocol/openid-connect/token"
token="eyJhbGciOiJIUz…RamQrAStW5FwYR6UhGBQ1v4Y"
 
[galaxy_server.galaxy]
url=https://galaxy.ansible.com
```
#### 2.3 - Define how you want your EE built

#### 2.4 - Add RHEL System Roles collection

#### 2.5 - Pull down base image

#### 2.6 - Build EE

#### 2.7 - Add EE to Automation Controller

* Copy the “Ansible Official Demo Project”:<br>
**Resources** → **Projects** → Find **“Ansible Official Demo Project”** → Click the "2 Papers" icon (at the very end of the row)
* Edit the copy "Ansible official demo project @ 00:00 PM":<br>
Click the “Pencil” icon 
* Update only the following fields:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<table>
    <tr>
      <th>Field</th>
      <th>Value</th>
    </tr>
    <tr>
      <td>NAME</td>
      <td>Workshop Mod</td>
    </tr>
    <tr>
      <td>DESCRIPTION</td>
      <td>Adds AC objects necessary for additional exercises</td>
    </tr>
    <tr>
      <td>SOURCE CONTROL URL</td>
      <td>https://github.com/mkbredem/product-demos</td>
    </tr>
  </table>

* Click **Save** button<br>
* Wait for "Last Job Status" indicator to go from "Waiting" to "Succesful".<br>
(You can also check the Project sync progress. Go to: **Views** -> **Jobs**)

### Step 2 - Run Job Template to add additional Projects and Job Templates

* Go to: **Resources** -> **Templates** -> **Add** -> **Add job template**<br>
* Fill out Job Template as follows:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<table>
    <tr>
      <th>Field</th>
      <th>Value</th>
    </tr>
    <tr>
      <td>NAME</td>
      <td>Workshop Setup</td>
    </tr>
    <tr>
      <td>INVENTORY</td>
      <td>Workshop Inventory</td>
    </tr>
    <tr>
      <td>PROJECT</td>
      <td>Workshop Mod</td>
    </tr>
    <tr>
      <td>EXECUTION ENVIRONMENT</td>
      <td>Control Plane Execution Environment</td>
    </tr>
    <tr>
      <td>PLAYBOOK</td>
      <td>setup_demo.yml</td>
    </tr>
    <tr>
      <td>CREDENTIALS</td>
      <td><strong>Type</strong>: Red Hat Ansible Automation Platform<br><strong>Name</strong>: Controller Credential</td>
    </tr>
  <tr>
      <td>VARIABLES</td>
      <td>demo: linux</td>
  </tr>
</table>

* Click **Save** button
* Click **Launch** button
* Review output while tasks complete

### Step 3 - Verify New Job Templates that were automatically created

* Go to: **Resources** -> **Templates**
* **Notice**: about 10 additional “LINUX/..” job templates were created.  Each job template provides an example of additional ansible use cases that can be performed/executed.<br><br>
We will be using some of these templates in upcomming exercise.

----

[Return to the Workshop Exercises](../README.md)