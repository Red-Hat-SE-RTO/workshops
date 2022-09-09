# Exercise 2.2 - Automation Controller Automating Itself

## Table of Contents

* [Objective](#objective)
* [Step 1 - Add "Workshop Mod" project to Controller](#step-1---add-workshop-mod-project-to-controller)
* [Step 2 - Run Job Template to add additional Projects and Job Templates](#step-2---run-job-template-to-add-additional-projects-and-job-templates)
* [Step 3 - Verify New Job Templates that were automatically created](#step-3---verify-new-job-templates-that-were-automatically-created)


## Objective

We have created some playbooks that will add new job templates to Automation Controller that we can then use to configure our ansible-builder environment.

In order to do this we are using the concept of Configuration as Code.  The Red Hat Ansible Community of Practice has created a collection that allows you create projects that will build out and configure your Automation Controller.  Bookmark the following link in order to read more about and explore the [redhat_cop.controller_configuration](https://external.ink?to=/github.com/redhat-cop/controller_configuration) collection.

### Step 1 - Add "Workshop Mod" project to Controller

* Copy the “Ansible Official Demo Project”:<br>
**Resources** → **Projects** → Find **“Ansible Official Demo Project”** → Click the "2 Papers" icon (at the very end of the row)
* Edit the copy of “Ansible Official Demo Project:<br>
Click the “Pencil” icon 
* Update only the following fields:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<table>
    <tr>
      <th>Field</th>
      <th>Value</th>
    </tr>
    <tr>
      <td>Name:</td>
      <td>Workshop Mod</td>
    </tr>
    <tr>
      <td>Description</td>
      <td>Adds AC objects necessary for additional exercises</td>
    </tr>
    <tr>
      <td>Source Control URL</td>
      <td>https://github.com/mkbredem/product-demos</td>
    </tr>
  </table>

* Click **Save** button<br>
Wait for “Workshop Mod” to finish syncing (this will start automatically)

### Step 2 - Run Job Template to add additional Projects and Job Templates

* Go to: **Resources** -> **Templates** -> **Add** -> **Add job template**<br>
* Fill out Job Template as follows:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<table>
    <tr>
      <th>Field</th>
      <th>Value</th>
    </tr>
    <tr>
      <td>Name:</td>
      <td>Workshop Setup</td>
    </tr>
    <tr>
      <td>Inventory</td>
      <td>Workshop Inventory</td>
    </tr>
    <tr>
      <td>Project</td>
      <td>Workshop Mod</td>
    </tr>
    <tr>
      <td>Exec Env:</td>
      <td>Control Plane Execution Environment</td>
    </tr>
    <tr>
      <td>Playbook:</td>
      <td>setup_demo.yml</td>
    </tr>
    <tr>
      <td>Credentials</td>
      <td>**Type**: Red Hat Ansible Automation Platform<br>**Name**: Controller Credential</td>
    </tr>
  <tr>
      <td>Extra vars:</td>
      <td>demo: linux</td>
  </tr>
</table>
* Click **Save** button
* Click **Launch** button

### Step 3 - Verify New Job Templates that were automatically created

* **Resources** -> **Templates**
* Notice: about 10 additional “LINUX/..” job templates were created.  Each job template provides an example of additional ansible use cases that can be performed/executed.

----

[Click here to return to the Ansible for Red Hat Enterprise Linux Workshop Exercise Menu](../README.md)