# Exercise 2.3 - Add Execution Environment for RHEL System Roles

## Table of Contents

* [Objective](#objective)
* [Step 1 - Run “LINUX / Setup Builder”](#step-1---run-linux--setup-builderr)
* [Step 2 - Create custom Execution Environment with RHEL System Roles collection](#step-2---create-custom-ee-with-rhel-system-roles-collection)
    * [2.1 - Access Terminal](#21---access-terminal)
    * [2.2 - Tell builder where to look for collections](#22---tell-builder-where-to-look-for-collections)
    * [2.3 - Define how you want your EE built](#23---define-how-you-want-your-ee-built)
    * [2.4 - Add RHEL System Roles collection](#24---add-rhel-system-roles-collection)
    * [2.5 - Pull down base image](#25---pull-down-base-image)
    * [2.6 - Build EE](#26---build-ee)
    * [2.7 - Add EE to Automation Controller](#27---add-ee-to-automation-controller)

## Objective

In exercise 2.2, the "LINUX / Setup Builder" job template was created.  Now we will execute this job template to build out and Ansible Builder environment on our controller node (**ansible-1** in **Workshop Inventory**). 


### Step 1 - Run “LINUX / Setup Builder”

### Step 2 - Create custom EE with RHEL System Roles collection

#### 2.1 - Access Terminal

#### 2.2 - Tell builder where to look for collections

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