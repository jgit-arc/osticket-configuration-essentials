<p align="center">
<img src="https://i.imgur.com/0KdiDRX.png" />
</p>

# osTicket - Configuration Essentials

This is a continuation of the *osTicket: Getting Started* repo found [here](https://github.com/jgit-arc/osticket-getting-started). The goal of this walkthrough is to provide hands-on experience with osTicket by configuring roles, departments, teams, agents, SLAs, etc., to simulate a real, working environment.

I am using a Windows virtual machine hosted on Microsoft Azure. The VM is named `osticket-vm` and runs Windows 10 Pro (2 vCPUs, 8 GB RAM). This guide does not delve into Azure-specifics or virtual machine setup. However, these steps will work on any version of Windows 10, whether running on a VM or not.

---

## Accessing osTicket

<p>
<img src="https://i.imgur.com/p7433G3.png"/>
</p>

osTicket has two URLs you will use frequently:
- localhost/osTicket/scp/login.php
- localhost/osTicket

The admin/analyst login is where all of the setup and configuration happens. The end-user login is how anyone working with the software would access it normally. In this and the following walkthrough, I will cover the functionality of both.

---

## 2. Agent Panel vs Admin Panel

<p>
<img src="https://i.imgur.com/JHMKsFw.png" />
<img src="https://i.imgur.com/bCsTpgT.png" />
</p>

If you have not done so already, go to the admin login and sign in as an admin using the credentials you created from the previous walkthrough. While logged in as an admin, you have access to two panels: **Agent Panel** and **Admin Panel**. 

- The **Admin Panel** allows you to configure settings.
- The **Agent Panel** more closely represents the end-user experience, allowing you to create, read, and edit tickets.

To determine which panel you are on, look at the toggle in the top-right corner:
- If it shows "Agent Panel," you are currently on the Admin Panel (and vice versa).

---

## 3. Configure Roles

<p>
<img src="https://i.imgur.com/SatJE2o.png"/>
</p>

From the **Admin Panel**, click **Agents**, then click **Roles**. By default, osTicket includes varying levels of role access. These can be modified, or you can create your own.

For example, the "Expanded Access" role allows users to do everything except delete a ticket or mark it as answered. Roles can be assigned to departments and individuals.

1. From the **Agents** tab, click **Add New Role**.
2. Name the role (e.g., `Main Admin`).
3. Click the **Permissions** tab.
4. Select permissions for the role. For this walkthrough, select all permissions under the **Tickets**, **Tasks**, and **Knowledgebase** tabs.
5. Click **Add Role**.

---

## 4. Configure Departments

<p>
<img src="https://i.imgur.com/YKZQAPf.png"/>
</p>

From the **Admin Panel**, click **Agents**, then click **Departments**.

1. Click **Add New Department**.
2. Click the **Settings** tab and configure the following:
   - **Parent:** Top Level Department
   - **Name:** SysAdmins
3. Leave other settings as default and click **Create Dept**.

---

## 5. Configure Teams

<p>
<img src="https://i.imgur.com/nNXihjE.png"/>
</p>

Teams allow users from different departments to be grouped. For example, one team may handle billing while another manages online support.

1. From the **Admin Panel**, click **Agents**, then click **Teams**.
2. Click **Add New Team**.
3. Under the **Team** tab, configure:
   - **Name:** Online Banking
4. Leave other settings as default and click **Create Team**.
5. Under **Dashboard > Settings**, uncheck **Registration Required** to simplify the walkthrough.

---

## 6. Configure Agents

<p>
<img src="https://i.imgur.com/c0bcea0.png" />
<img src="https://i.imgur.com/J3QASPM.png" />
</p>

Agents are users that help resolve tickets. 

1. From the **Admin Panel**, click **Agents**.
2. Click **Add New Agent**.
3. Under the **Account** tab, configure:
   - **Name:** Jane Doe
   - **Email Address:** janedoe@anyemail.com
   - **Username:** jane
   - (Optional) Set a password manually if desired.
4. Under the **Access** tab, configure:
   - **Department:** SysAdmins
   - **Role:** Main Admin
5. Under the **Teams** tab, assign:
   - **Online Banking**
6. Click **Create** and repeat these steps for another agent, "John Doe," using the following details:
   - **Department:** Support
   - **Role:** Main Admin

---

## 7. Configure Users

<p>
<img src="https://i.imgur.com/O5JaGq7.png"/>
</p>

Users are the customers who submit tickets.

1. From the **Agent Panel**, click **Users**.
2. Click **Add User**.
3. Configure:
   - **Email Address:** karen@upsetuser.com
   - **Full Name:** Karen
4. Leave other settings as default and click **Add User**.

---

## 8. Configure Service Level Agreements (SLAs)

<p>
<img src="https://i.imgur.com/9PuudvQ.png" />
</p>

SLAs prioritize tasks based on urgency.

1. From the **Admin Panel**, click **Manage > SLA**.
2. Click **Add New SLA Plan**. Create three SLAs with the following configurations:

   - **Sev-A:** Grace Period: 1 hour, Schedule: 24/7
   - **Sev-B:** Grace Period: 4 hours, Schedule: 24/7
   - **Sev-C:** Grace Period: 8 hours, Schedule: Monday-Friday 8 AM - 5 PM (US Holidays)

3. Leave other settings as default and click **Add Plan**.

---

## 9. Configure Help Topics

<p>
<img src="https://i.imgur.com/aE8hhFe.png"/>
</p>

Help Topics categorize tickets for better management.

1. From the **Admin Panel**, click **Manage > Help Topics**.
2. Click **Add New Help Topic** and configure:
   - **Topic:** Business Critical Outage
   - **Parent Topic:** Report a Problem
3. Repeat this process for the following topics:
   - **PC Issues** (Parent Topic: Report a Problem)
   - **Equipment Request** (Parent Topic: General Inquiry)
   - **Password Reset** (Parent Topic: Report a Problem)
   - **Other** (Parent Topic: General Inquiry)
4. Leave other settings as default and click **Add Topic** for each.

---
