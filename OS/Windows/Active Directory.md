#Windows
### 1. Basics of Active Directory

#### AD Structure:

- **Forest:**
  - The top-level logical container in an Active Directory environment. A forest can contain multiple domains, and it establishes a security boundary within which all objects (users, groups, computers, etc.) are stored. All domains within a forest share a common schema, configuration, and global catalog.

- **Domain:**
  - A logical grouping of objects within a forest, typically representing a specific organizational structure or geographical location. Domains share a common security policy and authentication system. Each domain has its own database of objects and can have trust relationships with other domains within the forest.

- **Organizational Units (OUs):**
  - Containers within a domain used to organize objects for easier management. OUs can mirror the organization's hierarchy, such as by departments or locations, allowing administrators to apply group policies and delegate administrative control at a granular level.

- **Domain Controller (DC):**
  - A server in a domain that hosts the Active Directory Domain Services (AD DS) role. Domain controllers store the AD database, authenticate users, enforce security policies, and replicate directory information to other domain controllers within the same domain.

#### Key Concepts:

- **LDAP (Lightweight Directory Access Protocol):**
  - A protocol used by Active Directory to access and manage directory information services over an IP network. LDAP is widely used to query and modify the directory and is the backbone for many directory services beyond AD. AD is often referred to as an LDAP-compliant directory service.

- **Kerberos Authentication:**
  - The default authentication protocol used by Active Directory. Kerberos provides secure authentication through the use of tickets and secret-key cryptography, ensuring that credentials are not sent over the network in plain text. This protocol also supports mutual authentication, where both the user and the server authenticate each other.

- **Global Catalog (GC):**
  - A distributed data repository that contains a partial, read-only replica of all objects in every domain within a multi-domain forest. The Global Catalog allows users and applications to locate objects across domains without needing to know their specific location, improving query performance and efficiency. Global Catalog servers are crucial in multi-domain environments for user logins and directory searches.

### 2. User and Group Management

#### User Account Management:

- **Create a New User:**
  - To create a new user account in Active Directory, you can use either the GUI (Active Directory Users and Computers) or command-line tools like `dsadd`.
  - **Example (Command Line):**
```bash
dsadd user "CN=John Doe,OU=Users,DC=example,DC=com" -samid jdoe -pwd Password123
```
- **CN (Common Name):** Specifies the user's name.
- **OU (Organizational Unit):** Specifies the organizational unit where the user will be created.
- **DC (Domain Component):** Represents the domain's hierarchical path.
- **samid:** Sets the user's logon name.
- **pwd:** Sets the user's password.

- **Reset User Password:**
  - To reset a user’s password in Active Directory, use the following command:
```bash
dsmod user "CN=John Doe,OU=Users,DC=example,DC=com" -pwd NewPassword123
```
 - **dsmod user:** Modifies the properties of an existing user.

- **Unlock User Account:**
  - If a user account is locked out due to multiple failed login attempts, you can unlock it using the `net user` command:
```bash
net user jdoe /domain /active:yes
```
- **/active:yes:** Reactivates the user account if it is locked.

#### Group Management:

- **Create a New Group:**
  - You can create security or distribution groups in Active Directory to manage user permissions and email distribution lists.
  - **Example (Command Line):**
```bash
dsadd group "CN=IT Group,OU=Groups,DC=example,DC=com"
```
- **dsadd group:** Creates a new group in Active Directory.
 - **Group Types:** Security groups are used for permissions, while distribution groups are used for email distribution.

- **Add User to Group:**
  - Adding a user to a group is crucial for managing permissions across resources.
  - **Example (Command Line):**
```bash
dsmod group "CN=IT Group,OU=Groups,DC=example,DC=com" -addmbr "CN=John Doe,OU=Users,DC=example,DC=com"
```
- **dsmod group:** Modifies an existing group's properties.
 - **-addmbr:** Adds a member to the group.

- **Remove User from Group:**
  - To remove a user from a group, you can use a similar command:
```bash
dsmod group "CN=IT Group,OU=Groups,DC=example,DC=com" -rmmbr "CN=John Doe,OU=Users,DC=example,DC=com"
```
- **-rmmbr:** Removes a member from the group.

#### Best Practices:
- **Use Descriptive Naming Conventions:** Clearly identify users, groups, and OUs to simplify management.
- **Delegate Group Management:** Assign group management responsibilities to specific users or admins to decentralize administration.
- **Regular Audits:** Periodically review group memberships to ensure that only authorized users have access to sensitive resources.

### **3. Security and Permissions**

#### **NTFS Permissions:**

- **Set NTFS Permissions:**
  - NTFS permissions control access to files and folders on an NTFS-formatted partition. You can set these permissions using the `icacls` command.
  - **Example:**
```bash
icacls "C:\Folder" /grant JohnDoe:F
```
- **icacls:** Command used to display or modify access control lists (ACLs) on files or directories.    
- **JohnDoe:F:** Grants Full Control permission to the user `JohnDoe`.

- **View NTFS Permissions:**
  - To view the current NTFS permissions on a file or folder:
```bash
icacls "C:\Folder"
```
- This command displays the ACLs for the specified directory or file.

- **Modify NTFS Permissions:**
  - You can modify existing NTFS permissions using the same `icacls` command:
```bash
icacls "C:\Folder" /remove JohnDoe
```
- **/remove JohnDoe:** Removes the permissions for the user `JohnDoe` on the specified folder.

#### **Group Policy Objects (GPOs):**

- **Create a GPO:**
  - Group Policy Objects are used to manage and configure operating system settings, application settings, and user settings across a domain.
  - **Example (PowerShell):**
```bash
New-GPO -Name "Password Policy"
```
- **New-GPO:** Creates a new Group Policy Object.
- **-Name "Password Policy":** Specifies the name of the new GPO.

- **Link GPO to an OU:**
  - After creating a GPO, you need to link it to an OU where it will be applied.
  - **Example (PowerShell):**
    ```bash
    New-GPLink -Name "Password Policy" -Target "OU=Users,DC=example,DC=com"
    ```
    - **New-GPLink:** Links a GPO to a specific organizational unit.
    - **-Target:** Specifies the target OU where the GPO will be applied.

- **Edit GPO Settings:**
  - To edit a GPO, use the Group Policy Management Console (GPMC) or PowerShell. Common settings include password policies, account lockout policies, and software restrictions.
  - **Example (Editing Password Policy via GPMC):**
    - Navigate to **Computer Configuration** > **Policies** > **Windows Settings** > **Security Settings** > **Account Policies** > **Password Policy**.
    - Modify settings such as **Minimum Password Length**, **Password Complexity Requirements**, etc.

#### **Security Groups:**

- **Create a Security Group:**
  - Security groups are used to assign permissions to resources in Active Directory. You can create them using PowerShell or the GUI.
  - **Example (PowerShell):**
    ```bash
    New-ADGroup -Name "SecurityGroup" -GroupScope Global -GroupCategory Security -Path "OU=Groups,DC=example,DC=com"
    ```
    - **New-ADGroup:** Creates a new security or distribution group.
    - **-GroupScope Global:** Sets the group scope (Global, DomainLocal, or Universal).
    - **-GroupCategory Security:** Specifies that this is a security group.
    - **-Path:** Specifies the OU where the group will be created.

- **Assign Permissions to Security Groups:**
  - Once a security group is created, you can assign it permissions to resources like files, folders, and printers.
  - **Example (NTFS Permissions with Group):**
    ```bash
    icacls "C:\Folder" /grant SecurityGroup:R
    ```
    - **SecurityGroup:R:** Grants Read permission to the `SecurityGroup` on the specified folder.

#### **Best Practices:**

- **Least Privilege:** Always follow the principle of least privilege, granting users and groups only the minimum permissions they need to perform their tasks.
- **Use Security Groups for Permissions:** Instead of assigning permissions to individual users, assign them to security groups. This simplifies management and enhances security.
- **Regularly Review Permissions:** Conduct regular audits to ensure permissions are correctly assigned and remove unnecessary permissions promptly.

This section covers the essentials of security and permissions management in Active Directory, focusing on NTFS permissions, Group Policy Objects, and Security Groups, which are critical for maintaining a secure and well-managed AD environment.