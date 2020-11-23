# eLabFTW Overview Guide

> Author: [Richard Hohensinner](mailto:richard.hohensinner@tugraz.at)

# - Actors & Permissions:

|                                | SysAdmin | Admin | User |
| :----------------------------: | :------: | :---: | :--: |
|   Modify Profile Information   |    x     |   x   |  x   |
|          Use Todolist          |    x     |   x   |  x   |
| Create/Edit/Delete experiments |    x     |   x   |  x   |
|       Upload to Database       |    x     |   x   |  x   |
|           Add Users            |    x     |   x   |      |
|         Create Groups          |    x     |   x   |      |
|    Add database item types     |    x     |   x   |      |
|    Define Experiment Status    |    x     |   x   |      |
|          Create Teams          |    x     |       |      |
|        System Settings         |    x     |       |      |
|   Security & Email Settings    |    x     |       |      |



## SysAdmin:

- Atleast 1 per eLab instance

- On top of the hierachy, system wide access

- Has access to all Teams, Groups and Users as well as System Settings and Accounts.

- Accessible through the SysAdmin Panel Button (Bottom left)

  

### Permissions:

- Generate usage statistics (e.g. Last Login from every User)
- Make public announcements (Pop-Up messages displayed in websites)

- Change general Language of the instance (can be overwritten by each user)
- Add new & Edit existing Teams.
- Manage Users (add, edit, remove, validate, add/restrict permissions and reset passwords)
- Modify teams which users are assigned/have access to
- Modify the Timestamping service
- Manage Security Settings (e.g. users need validation after registration, restrict email domains "@tugraz.at" or number of allowed to fail login attempts)
- Create automated Email service for eLabFTW (e.g. verification email after registration or "Forgot password" emails)
- Create SAML login for users (= Forwarding of TU/KF login sessions) This can also be used to automatically create accounts based off of the Identity Provider's authentication session. (Name, Email, Status[Student, Professor, External])

---

## Admin:

- Arbitrary number of Admins possible
- Don't see further than the team(s) they are assigned to
- Act as **Teamleader**
- Accessible through the Admin Panel Button (Bottom left)

### Permissions:

- Can configure Team settings (enable/disable anonymous access, user read/write/delete rights)
- Create a custom link (e.g. to an institute website) by modifying the "Documentation button" in the settings.
- Manage Groups (create, delete)
- Administrate Users (in team's scope) 
- Add new users. 
- Modify/Delete existing users. 
- Promote or Demote users (Admin <-> User)
- Edit possible Status of experiments ("In Preparation", "Running", "Success", "Fail", "Canceled" etc.)
- Edit possible Database items (e.g. "Dataset", "Notes", "Report"...)
- Define Experiment templates to align with best-practices or individual standards
- Import files to the Database (.csv or .zip files)
- Define Tags for the team. Tags are used to make experiments easily identifiable and filterable (e.g. GroupX, TypeY, DateZ - StudentTeam1, LectureExperiment, 29102020)

---

## User:

- Users are the basis of the hierarchy
- Always have to be assigned to at least one team
- Permissions depend on rights given by the team's Admin

### Permissions:

- Set individual Language
- Display configurations (e.g. 10 experiments per page)
- Individual Keyboard Shortcuts
- PDF/Document modification
- Additional general settings (e.g. show team's experiments, set default values for visibility of experiments...)
- Account update - New Password, identity modifications, add additional contact information
- Create personal experiment templates
- Generate and change API keys.

# Teams & Groups:

## Teams:

Teams are used to organize members of eLabFTW. Each team consists of at least one member, beside that, the team size can be arbitrarily high.

In practice, teams are used to enable its members to collaborate, share information and restrict access to the outside (guests, other teams etc.).

Access rights, team settings and member privileges can be configured individually for each team by an [Admin](#admin).

Teams also feature to create scheduling tasks, define custom experiment templates, member informations and a built-in email system. 

eLabFTW users can be part of multiple teams at a time. The current team persona can be chosen after logging in, but cannot switch during a session. Changing the current team requires a new session (logout + login). The primary purpose of this implementation is to not confuse users about their current team status. Without this, users might share important information with other teams unintentionally, or Admins might configure the wrong team by accident.

Teams are organized by the SysAdmin by the means of creation and deletion - After creation Admins of teams can then invite or remove members. This also enables to usage of team-wise administrators, by restricting their access to just one team. The actor status of a eLabFTW user can not change between different teams. (Meaning, an [Admin](#admin) of one team cannot be just a user of another team)

It is not possible to access eLabFTW without being part of at least one team.

## Groups:

Groups in eLabFTW are a subsets of teams. Groups are optional and managed by Admins and can be arbitrarily big. It is also possible to create groups across multiple teams.

Groups are primarily used for categorization. Beside that groups can not be used to manage access rights or privileges and are thus more of a cosmetic feature. 

An example use case could be: 80 students are part of a team and should build groups of 4. The Admin (Professor) can then create 20 groups and assign 4 students to each group. After that the students can see the groups they were assigned to and collaborate. 

# Experiments:

Experiments are the centerpiece of eLabFTW. They enable users to document and record real experiments in a digital way.  The experiments function features a built-in text editor, a tool to create and upload drawing, attach files, add/set tags, manage read/write permissions, share the experiment via a link, lock & unlock possibilities, select different status, define individual steps, link items from the database and a way to officially timestamp the experiment.

After an experiment was timestamped, which is the final step, it can no longer be modified by anybody in any way. Timestamped experiments can then be exported as PDF files or ZIP directories.

With standard settings, every user of every team can create experiments.  The permissions of users to grant access rights to other members or teams is set by the [Admin](#admin).

As already mentioned in Teams, experiment templates can be created by an Admin and selected in the Team tab by users. Because experiments can differ enormously between disciplines it is advised to use templates for different fields of experiments.

# Database:

The database in eLabFTW is used to share data with other users. Read and write permissions of database items can be individually set for each item. This makes it possible to share certain data with everyone using the instance of eLabFTW, other data just with the team and specific data just with yourself (e.g. private experiment). 

Different types of items can be defined by an Admin. There are 2 essentially different types of items: bookable and non-bookable items. Non-bookable types of items are generally standard items that can be created for the sole purpose of uploading data. This could be listings, guides, text based data, datasets, images, videos or any other kind of information. Bookable types of items one the other hand are used for events or time related tasks. An example for a bookable type could be "Experiment preparation". A user could then create an instance of this type called "E.p. Experiment A" and add a location in the description. After that the user can book this item at the Team tab (e.g. Monday 10:00 - 10:30) to let other team members know when and where the preparation takes place.

The creation of database items is very similar to the creation of experiments. Database items must have a type, beside that, they are individually modifiable as desired.

# Use Cases:

1. **Creating a new Team (SysAdmin):**

   - Navigate to the SysAdmin Panel (bottom left)
   - Navigate to the TEAMS-Tab at the top
   - Enter your team name under "Add a New Team" and click save:
   - ![Team Creation](img/01_new_team.png "1) Creating a new Team")

   - Now the team will be listed under "Edit Existing Teams"

   - There you can set a Team Organization ID and configure privacy settings (visible to register, or not):

   - ![Team Config](img/01_new_team_config.png "2) Configure a (new) Team")

     ---

   

2. **Assigning Teams to members (SysAdmin):**

   - Navigate to the SysAdmin Panel (bottom left)

   - Navigate to the USERS-Tab at the top

   - Either type a known User Name into the search bar, or leave it empty to retrieve all users

   - Click on the search button

   - For every searched User detailed information is displayed:

   - ![Search Results](img/02_user_search.png "3) User search results")

   - Click on the "Add Team" button of the user you want to add to a Team:

   - ![Add Team](img/02_add_user_team.png "4) User add Team")

   - Select the Team in the drop-down menu

   - Click on "Edit"

   - Search the user you added again, if you want to verify that the user has been added to the Team:

   - ![Verify Add Team](img/02_team_verification.png "5) User add verification")

   - (This process of Removing a team works exactly like this as well)

     ---

     

3. **Register new users to a Team (Admin):**

   - Navigate to the Admin Panel (bottom left)

   - Navigate to the USERS-Tab at the top

   - Under "Add Account" first select the Team you want to register a new User to

   - Then fill out the User's Email, Name and Privileges, you want to add:

   - ![Register new User](img/03_user_register.png "6) User registration")

   - The user will then have to use the "Forgot password" button at the login page to set a password

     ---

     

4. **Creating a Group and assigning members (Admin):**

   - Navigate to the Admin Panel (bottom left)

   - Navigate to the GROUPS-Tab at the top

   - Enter a Group Name and click on "Create"

   - The new Group will now be listed under "Existing Groups":

   - ![Group Creation](img/04_group_creation.png "7) Group Creation")

   - In the "Add user" search bar start typing the name of the user you want to add

   - A dynamic list with suggestions will appear - select the desired user:

   - ![Group add User](img/04_group_add_users.png "8) Group add User")

   - Repeat this step until all users are added to the Group:

   - ![Group finished](img/04_group_finished.png "8) Group Finished")

   - (To rename a Group click on the Group Name - To delete a Group use the trash can icon on the right side)

     ---

5. **Adding an experiment status (Admin):**

   - Navigate to the Admin Panel (bottom left)
   - Navigate to the STATUS-Tab at the top
   - Enter the Name of the Status you want to add into the Name textbox
   - Optionally select a color or allow/reject Timestamping during this Status
   - Click on Create:
   - ![Status Creation](img/05_create_status.png "9) Create Status")
   - Use the Arrows to the right to drag&drop the Status to the desired place:
   - ![Status Placement](img/05_place_status.png "10) Place Status")
   - Additionally it is now possible to edit the Status (e.g. changing the Default status etc.)
   - To improve obviousness it is advised to keep the Status in a chronological order

6. **Defining a database item type (Admin):**

   - Navigate to the Admin Panel (bottom left)
   - Navigate to the TYPES OF ITEMS-Tab at the top
   - Fill out the Name textbox and optionally change the item type's color
   - Check the scheduler checkbox in case the item type should be bookable in the calender
   - Enter template information inside the text field below
   - Click on the Save button:
   - ![Type Creation](img/06_create_item_type.png "11) Create Type")
   - The new type of item is now selectable during the database item creation.
   - (Here the type of items can be edited or deleted.)

7. **Creating an experiment (User):**

   - Navigate to the EXPERIMENTS-Tab at the top
   - Click on the Create button (top-right)
   -  Fill out the any information available [(Experiments)](#experiments):
   - ![Exp Creation1](img/07_create_an_experiment.png "12) Create Experiment")
   - Open the permissions with the three dots button (top-right):
   - ![Exp Creation2](img/07_open_permissions.png "13) Open Permissions")
   - Set the Permissions:
   - ![Exp Creation3](img/07_set_permissions.png "13) Set Permissions")
   - Click on Close
   - Click on the Save and Back button, then navigate back to the EXPERIMENTS-Tab.
   - Your newly created Experiment will be shown in the list:
   - ![Exp Creation4](img/07_show_experiment.png "14) Show Experiment")
   - Depending on the permissions set, your Everyone/Team/Group/You can see and edit the Experiment by selecting it here.

8. **Creating a database item (User):**

   - Navigate to the DATABASE-Tab at the top
   - Click on the Create button (top-right)
   - Select a Item Type
   - Fill out all information available (similar to 7. Creating an Experiment):
   - ![Item Creation1](img/08_create_an_item.png "15) Create Item")
   - Set the permission similar to creating an experiment
   - Click on Save and go back
   - Verify that the item was created successfully:
   - ![Item Creation2](img/08_check_results.png "16) Check Item")

9. **Book a database item (User):**

   - Make sure you have a schedulable item available - if not create one.
   - Navigate to the TEAM-Tab at the top
   - Select the Scheduler-Tab
   - Select an equipment from the drop-down menu (= schedulable item)
   - Set the time frame for the booking by clicking into the calender (start time) and dragging the mouse to the destination (end time) and optionally add a comment:
   - ![Item Scheduling](img/09_schedule_item.png "17) Schedule Item")
   - Your chosen time slot will now be booked in the calender being visible to the team:
   - ![Item Scheduling2](img/09_check_result.png "18) Check Item")

10. **Timestamp and export an experiment (User):**

    - Navigate to the EXPERIMENTS-Tab at the top
    - Click on the experiment you want to timestamp
    - Make sure the experiment is in an timestampable state, if it is not, use the Pen icon to edit the experiment and change the status of the experiment to a valid state (e.g. success/failed)
    - Click on the Calender Icon to initiate the timestamp:
    - ![Experiment Finish1](img/10_timestamp_experiment.png "19) Timestamp Experiment")
    - Read the message carefully - once the experiment has been timestamped it can no longer be edited in the future:
    - ![Experiment Finish2](img/10_verify_timestamppng.png "20) Verify Timestamp")
    - Your Experiment is now timestamped
    - Use the Page icons to export the experiment to either a pdf file or a zip repository:
    - ![Experiment Finish3](img/10_export_to_pdf.png "21) Experiment pdf") 
    - The exported pdf will automatically be opened inside the browser window:
    -  ![Experiment Finish4](img/10_check_pdf.png "22) Check pdf") 
    - From here the pdf file can be downloaded or printed
    - (When selecting the export to ZIP repository a download will start automatically)

# Versions:

eLabFTW version: 3.5.6

Docker image version: 2.0.1

MySQL database structure version: 55

OS: Linux

PHP version: 7.3.22

Maximum File Size: 100 MB

Timezone: Europe/Paris

