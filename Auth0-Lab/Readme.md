# Auth0 Identity Lab

This lab demonstrates how to use the Auth0 web interface to simulate identity and access management tasks commonly performed by IT Helpdesk Analysts or System Administrators. It walks through the process of creating an application, setting up users and roles, enabling MFA, and testing the login experience.

---

## Lab Setup Overview

**Platform:** Auth0 Developer Tenant  
**Interface:** Auth0 Admin Console (UI only)  
**MFA Method:** One-Time Password (TOTP) via Google Authenticator

---

## Step-by-Step Walkthrough

### 1. Create a New Application

Created a native application named `Isaac Test Application` within the Auth0 dashboard to simulate internal SSO functionality.

<img width="801" height="723" alt="(1) Creating an Application" src="https://github.com/user-attachments/assets/937511a9-373b-4ff9-9cbb-b8e2439bef74" />


### 2. Add Roles

Added three roles to reflect common organizational user types:

- Admin  
- Employee  
- Intern

<img width="1762" height="776" alt="(2) Adding Roles" src="https://github.com/user-attachments/assets/d6bfbfd5-0044-4629-a445-78b33c7caa4f" />

### 3. Create Users

Created three users and mapped them to roles:

- `jane.admin@isy-labs.com` → Admin  
- `mark.analyst@isy-labs.com` → Employee  
- `chris.intern@isy-labs.com` → Intern

<img width="1920" height="799" alt="(3) Adding Users" src="https://github.com/user-attachments/assets/bddd2b90-df02-4556-b30e-57260ab6ee0c" />


### 4. Assign Roles to Users

Opened each user profile and assigned the appropriate role under the Roles tab.

### 5. Enable MFA

Enabled One-Time Password authentication under **Security > Multi-factor Auth**. This required users to enroll in an authenticator app like Google Authenticator during login.

<img width="1881" height="1021" alt="(4) Configuring MFA using Auth0" src="https://github.com/user-attachments/assets/0e621730-271e-4223-94e5-771a52535c80" />

### 6. Test the Login Flow

Tested the login as `jane.admin@isy-labs.com`. Successfully signed in, entered an OTP, and was redirected to the configured callback URL. A 404 was expected since the app is not hosted, but the presence of an Auth0-issued code in the URL confirmed success.

<img width="1282" height="1050" alt="image" src="https://github.com/user-attachments/assets/84308a87-0cf6-4140-aabd-53224aaa6917" />

<img width="1352" height="702" alt="image" src="https://github.com/user-attachments/assets/88b0705c-94e8-4115-b1cd-b4bae22503a0" />

---

## Skills Demonstrated

- User provisioning through identity provider interface  
- Role-based access control configuration  
- MFA policy enforcement  
- Realistic UI navigation and workflow understanding

---

This lab was intentionally lightweight but realistic. It demonstrates clear familiarity with the Auth0 interface and core IAM concepts without requiring backend development or scripting.
