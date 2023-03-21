# B3 Dev - CRM API “light”
## Introduction
Built an API for a CRM app. 

It is a very basic CRM: there are pages, with different types of content, users with permissions, etc. 

## Resources

### User
- Unique ID
- E-mail 
- Password
- First name 
- Last name
- Role (which gives permissions)

### Role
 - Unique ID
- Name (admin / manager / editor)
- Permissions (CRUD) per resource

### Page
- Unique ID
- Title
- Content
- Unique URL slug
- Creator
- Users who have modified it
- Date and time it was published
- Status: draft,  published

### Navigation Menu
- Unique ID
- Name
- Hierarchical (nested) list of pages (like a directory tree on the fie system). 

### Form (BONUS)
- Unique ID
- Name
- Ordered list of fields

### Field
- Type (single or multi line text, radio, select, checkbox)
- Options (if necessary 
- Label
- Default value 

## Requirements
- You don’t need to validate the content in pages, which will contain some form of custom markdown allowing referencing forms, pages, etc. 
- You only have to provide a level 2 REST API, but if you wish to, you can build a level 3 REST API. 
- All resources must be paginated with either limit/offset or limit/page query params. 
- Every endpoint should provide through query params filtering and sorting (single sort, but you can go for multi sorting). 
- You need to provide session management through sign-in process (we suppose sign-up doesn’t exist and is handle by admin roles by manually adding users) and use JWT for session persistence. 
- You need to check a user’s permission for every request and secure properly actions on resources as defined by permissions (e.g a public info must be available without a session, but changing a page content would be forbidden). 
- You don’t need to handle form submission content. 
- BONUS: All response must provide a `result` and `meta` data with a total count of the current requested list (taking into account all the filters, etc.) beyond pagination. 
- BONUS: handle password reset without storing any token in the database. 

## Permissions

Not all resources require permissions (this is a hint to help you make the right decision for designing your API). 

### User
- Create: admin
- Read: admin or self (your own info when logged in)
- Update: admin or self
- Delete: admin or self

### Page
- Create: admin, manager
- Read: all (published), logged users (draft)
- Update: logged users
- Delete: admin, manager

### Navigation Menu
- Create: admin, manager
- Read: all
- Update: admin, manager
- Delete: admin, manager

### Form (BONUS)
- Create: admin, manager
- Read: all
- Update: admin, manager
- Delete: admin, manager
