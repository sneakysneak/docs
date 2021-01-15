---
title: Moodle Authentication
sidebar: cyclr_sidebar
permalink: moodle-connector
tags: [connector]
---

## Partner Setup

To authenticate the Moodle connector you will need an `API Token`. This is obtained by setting up an application within your Moodle environment.

### Setting up an application in Moodle

1. Follow the steps in this guide for using [Web Services](https://docs.moodle.org/310/en/Using_web_services) in Moodle.
2. The only protocol you will need to enable in *Step 2* is `REST`.
3. For *Step 5* you will need to enable the following functions to be able to use all Cyclr methods:


| Service Functions               |
| ------------------------------- |
| core_group_add_group_members    |
| core_group_assign_grouping      |
| core_group_create_groupings     |
| core_group_create_groups        |
| core_group_delete_group_members |
| core_group_delete_groupings     |
| core_group_delete_groups |
| core_group_get_activity_allowed_groups |
| core_group_get_activity_groupmode |
| core_group_get_course_groupings |
| core_group_get_course_groups |
| core_group_get_course_user_groups |
| core_group_get_group_members |
| core_group_get_groupings |
| core_group_get_groups |
| core_group_unassign_grouping |
| core_group_update_groupings |
| core_group_update_groups |
| enrol_manual_enrol_users |
| core_course_get_courses |
| core_user_create_users |
| core_user_get_users |
| gradereport_overview_get_course_grades |

4. For *Step 6* the following user capabilities are required:

| User Capability    |
| ------------------ |
| moodle/course:view |
| moodle/course:update |
| moodle/course:viewhiddencourses |
| moodle/course:managegroups |
| moodle/user:create |
| moodle/user:viewdetails |
| moodle/user:viewhiddendetails |
| moodle/course:useremail |
| moodle/user:update |
| enrol/manual:enrol |

5. Once the Moodle Web Service application has been created, you need to create a token, selecting the user with the above permissions, and the newly created service.
6. Once you have the token, you must enter it and the fully qualified domain to authenticate, e.g `https://sandbox.moodledemo.net/`