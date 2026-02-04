# Creating a Table for Configuration Records

## Overview
This repository demonstrates how a custom configuration table was created in ServiceNow to track Holographic Handheld Devices (HHDs). The lab focuses on extending the CMDB hardware model, adding a custom firmware field, configuring list and form layouts, and updating the application menu to support device management.

This configuration enables Cloud Dimensions to manage Infinity HHD devices, their assignments, and configuration details through a dedicated application module.

## Use Case
Cloud Dimensions requires a structured way to track Infinity HHD devices distributed during pilot and post-release phases. Each device must be associated with a user, configuration details, and support ownership to enable visibility and lifecycle tracking.

This walkthrough reflects how a ServiceNow administrator extended the CMDB to support custom hardware tracking while aligning with CMDB best practices.

## Features
- Custom CMDB table extending hardware
- Firmware version tracking
- Configured list and form layouts
- Dot-walked user email field
- Application menu and module updates
- Device assignment validation

## Technologies Used
- ServiceNow Platform
- Configuration Management Database (CMDB)
- Table & Column Administration
- Form Builder
- List Layout Configuration
- Application Menu & Module Management

## Implementation Walkthrough

### Step 1: Create the Holographic Handheld HHD Table
A new custom table named **Holographic Handheld HHD** was created in the Global scope to track Infinity devices.

The table was configured to extend **Hardware [cmdb_ci_hardware]**, ensuring inheritance of standard CMDB hardware attributes while supporting device-specific fields.

A new application menu entry labeled **HHD** was associated with the table to support navigation.

<img width="1904" height="380" alt="Screen Shot 2026-01-30 at 10 26 40 AM" src="https://github.com/user-attachments/assets/ecf21564-f865-4433-9cd7-fb80df1beb9c" />

### Step 2: Review Inherited Hardware Fields
After saving the table, the inherited fields from the hardware parent table were reviewed to confirm that standard CMDB attributes were available without duplication.

This validated that the table followed CMDB extension best practices.

### Step 3: Add the Firmware Version Field
A new string field labeled **Firmware version** was added to the HHD table.

The field was configured with a maximum length of **40 characters** to support version identifiers while maintaining consistency across records.

<img width="1904" height="417" alt="Screen Shot 2026-01-30 at 10 38 57 AM" src="https://github.com/user-attachments/assets/c8a2c5eb-acc9-42da-9ef0-fa26f7646ce7" />

### Step 4: Configure the HHD List Layout
The list layout for **Holographic Handheld HHDs** was configured to display the following columns in order:

- Name  
- Serial Number  
- Asset tag  
- Firmware version  
- Support group  
- Installed  
- Install Status  
- Assigned to  
- Comments  

This layout provided clear visibility into device ownership, configuration state, and support responsibility.

<img width="1904" height="671" alt="Screen Shot 2026-01-30 at 10 55 40 AM" src="https://github.com/user-attachments/assets/36e88a76-3d95-48d0-b561-83c202b057b1" />

<img width="1897" height="223" alt="Screen Shot 2026-01-30 at 10 57 58 AM" src="https://github.com/user-attachments/assets/199a79ca-80f0-4bbc-848e-1ffbf6c2ea49" />


### Step 5: Configure the HHD Form Layout
The HHD form view was configured using Form Builder to present key device attributes in a logical order.

The form included core identification fields, assignment details, firmware information, and operational status to support day-to-day device management.

<img width="1897" height="793" alt="Screen Shot 2026-01-30 at 11 03 08 AM" src="https://github.com/user-attachments/assets/a7634372-56a8-4402-8f0c-d45711c406f9" />

<img width="1897" height="439" alt="Screen Shot 2026-01-30 at 11 04 12 AM" src="https://github.com/user-attachments/assets/a33ba1b4-b7b4-4c9d-88cb-b380cf8cf55b" />

### Step 6: Add Assigned To Email via Dot-Walking
The **Assigned to.Email** field was added to the HHD form using dot-walking from the User table.

This allowed the assignee’s email address to automatically populate based on the selected user, reducing manual lookup and improving accuracy.

<img width="1897" height="797" alt="Screen Shot 2026-01-30 at 11 06 51 AM" src="https://github.com/user-attachments/assets/db7bbe64-c9ad-430c-94aa-801c9d87f201" />

<img width="1898" height="467" alt="Screen Shot 2026-01-30 at 11 30 01 AM" src="https://github.com/user-attachments/assets/3739c0a0-c420-4da7-b3ab-eb13c725dab2" />

### Step 7: Update the Application Menu
A new application module titled **Create New** was added to the HHD application menu.

The module was configured to open a new record form for the Holographic Handheld HHD table, allowing users to create device records directly from the menu.

The existing list module was renamed to **HHDs and Assignees** to better reflect its purpose.

### Step 8: Validate Navigation
The updated application menu was reviewed to confirm that both **HHDs and Assignees** and **Create New** modules displayed correctly.

<img width="1898" height="349" alt="Screen Shot 2026-01-30 at 11 24 36 AM" src="https://github.com/user-attachments/assets/20d3bc38-fcab-451d-8b2f-64f3551e49ec" />


## Lessons Learned
- Extending CMDB tables preserves data integrity and reduces duplication
- Custom fields should align with real operational needs
- List and form layouts significantly impact usability
- Dot-walking enables richer data visibility without additional tables
- Application modules improve navigation and adoption of custom tables
