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

### 3. Security and Permissions

#### NTFS Permissions:

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

#### Group Policy Objects (GPOs):

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

#### Best Practices:

- **Least Privilege:** Always follow the principle of least privilege, granting users and groups only the minimum permissions they need to perform their tasks.
- **Use Security Groups for Permissions:** Instead of assigning permissions to individual users, assign them to security groups. This simplifies management and enhances security.
- **Regularly Review Permissions:** Conduct regular audits to ensure permissions are correctly assigned and remove unnecessary permissions promptly.

### 4. Attacks and Mitigations

#### Pass-the-Hash (PtH) Attack:

- **Description:** In a PtH attack, attackers capture NTLM hash values and use them to authenticate as a user without knowing the actual password. This allows attackers to move laterally across the network.
- **Mitigation:**
  - Enforce the use of strong, complex passwords and multi-factor authentication (MFA) to make it harder for attackers to capture and reuse hashes.
  - Disable NTLM where possible and configure systems to use Kerberos authentication instead.
  - Implement account lockout policies to limit the number of login attempts and detect suspicious activity.
  - Regularly rotate and manage privileged account credentials to minimize the attack surface.

#### Pass-the-Ticket (PtT) Attack:

- **Description:** PtT attacks involve stealing and using Kerberos tickets, specifically Ticket Granting Tickets (TGTs), to authenticate as a user. Attackers can use this method to move laterally or escalate privileges within a domain.
- **Mitigation:**
  - Enforce the use of strong encryption for Kerberos tickets and reduce their lifetime to limit the window of exploitation.
  - Regularly clear Kerberos tickets from memory using tools like `klist` to prevent ticket theft.
  - Monitor Kerberos authentication traffic and detect unusual patterns indicative of PtT attacks.
  - Limit the use of privileged accounts and enforce strict access control policies.

#### Golden Ticket Attack:

- **Description:** A Golden Ticket attack occurs when attackers compromise the KRBTGT account, which is used to encrypt all Kerberos tickets in a domain. This allows them to forge TGTs for any user, effectively giving them unrestricted access to the network.
- **Mitigation:**
  - Regularly reset the KRBTGT account password to invalidate any forged tickets and disrupt ongoing attacks.
  - Implement strict monitoring for any unusual ticket activity or unauthorized domain controller communication.
  - Use tiered administrative models to reduce the likelihood of KRBTGT compromise and enforce least privilege on all accounts.

#### Silver Ticket Attack:

- **Description:** In a Silver Ticket attack, attackers forge a service ticket (TGS) for a specific service by compromising a service account, allowing them to access that service without authentication.
- **Mitigation:**
  - Ensure service accounts use strong, complex passwords and regularly rotate these passwords to minimize the risk of compromise.
  - Apply strong encryption (e.g., AES) for service tickets and enforce signing and encryption for all service accounts.
  - Monitor service account activity and audit the use of service tickets to detect potential Silver Ticket attacks.
  - Use managed service accounts (MSAs) to reduce the risk of password-based attacks on service accounts.

#### DCSync Attack:

- **Description:** A DCSync attack allows attackers with domain admin privileges to simulate the behavior of a domain controller and request password hashes from another domain controller. This enables them to obtain credentials for any user in the domain.
- **Mitigation:**
  - Limit the number of accounts with domain admin privileges and enforce the principle of least privilege.
  - Monitor and log replication requests to detect any unauthorized or suspicious replication activities.
  - Use tiered administrative models to reduce the attack surface and limit the impact of a compromised domain admin account.
  - Regularly audit and secure Active Directory replication permissions and configurations.

#### DCShadow Attack:

- **Description:** DCShadow attacks involve registering a rogue domain controller in the network, allowing attackers to inject malicious changes into the Active Directory database without detection.
- **Mitigation:**
  - Use secure administrative workstations (SAWs) for all high-privilege administrative tasks to reduce the risk of credential theft.
  - Monitor AD replication traffic and domain controller registration activities to detect unauthorized changes.
  - Regularly review and audit the list of domain controllers and ensure only authorized controllers are present in the environment.
  - Implement strong authentication and access controls for domain controller management.

#### [[Kerberoasting]]:

- **Description:** Kerberoasting is an attack targeting service accounts in Active Directory. Attackers request a service ticket for a service account and extract the ticket from memory to attempt offline cracking of the ticket's encryption, revealing the service account's password.
- **Mitigation:**
  - Ensure service account passwords are long, complex, and regularly updated to resist offline cracking attempts.
  - Configure service accounts to use strong encryption algorithms, such as AES, instead of weaker RC4 encryption.
  - Monitor and audit Kerberos ticket requests, especially for sensitive service accounts, to detect potential Kerberoasting activities.
  - Limit the privileges of service accounts and use managed service accounts (MSAs) to reduce the risk of credential theft.

#### Best Practices for Mitigation:

- **Regular Patching and Updates:** Keep domain controllers and other AD-related servers updated with the latest security patches to mitigate vulnerabilities that could be exploited by attackers.
- **Principle of Least Privilege:** Grant users and administrators only the permissions necessary for their roles, reducing the impact of compromised accounts or credentials.
- **Multi-Factor Authentication (MFA):** Enforce MFA for all privileged accounts to provide an additional layer of security against credential-based attacks.
- **Monitoring and Logging:** Implement continuous monitoring and logging of AD activities, including authentication attempts, group membership changes, and replication activities, to detect suspicious behavior.
- **Use Managed Service Accounts (MSAs):** Replace traditional service accounts with MSAs or group MSAs (gMSAs) to enhance security and eliminate password management issues.
- **Regular Security Audits:** Conduct regular security audits of AD configurations, Group Policy Objects (GPOs), user permissions, and security settings to identify and mitigate potential risks.

