---
title: Integration Template Versioning
sidebar: cyclr_sidebar
permalink: integration-template-versioning
tags: [getting-started]
keywords: versioning, locked, template management, deprecated, integration management, template version
---

To help you and your team organise and iterate your integrations we have introduced integration template versioning to the Cyclr Console.

The new feature allows you to create draft releases of an integration, so you can build it out and test new additions, before locking it as a Live release. 

![](./images/live-template-workflow.png)

While Live releases can no longer be edited, you can however create a copy of it in order to create an iterative new release. Once this has been built out as required it can be set as the new Live version of the workflow.

Combining this with our audit trail features, your whole team are able to build and work on integration templates, with their account details being assigned to a release for traceability.  



Template Releases Orientation 
-------------------

![](./images/Template-Release-Screen.png)

1)  Title of integration template you are working on

2)  Status of the template release

3)  Release notes for template version (click on text to add/edit)

4)  Audit trail (see who created the release and when)

5)  The applications used in the integration template release

6)  Promote draft release to Live button

7)  Edit template release in workflow builder button

8)  Run/test integration workflow release button

9)  Go to workflow release statistics button

10) Copy template release (can be used to create a new draft release, copied to another template or as a new template) 

11) Delete template release button

12) View template release in builder (Live and Deprecated releases are locked for editing) 



Published Integrations
---------------

One of the main advantages of using the versioning feature is for updating your published integrations without having to take them down.

Published integration templates will always provide the “Live” version of the template to your users, so you are able to create a draft version, make any necessary updates and promote to Live to make it accessible to new user installations - without any downtime.

![](./images/Integration-Template-Releases.png)


Copying Integration Templates
---------------

While Live template versions are automatically locked for editing you can quickly create a new identical, editable version by copying the template.

![](./images/live-template-workflow.png)

Upon clicking the copy button next to the template’s Live version in your Releases screen, you can add release notes or a custom version name/number, as well as being able to select where you want the new template to be copied to.

As standard, the default destination will be the current template’s releases, however, you are able to select other workflow template releases to copy your draft to. This allows you to quickly create new releases for similar workflow types (EG- If you are creating CRM integrations with your applications and have created one, copy it to a new template and swap out the CRM steps for the equivalent steps in another CRM connector.) 


Copying Integration Templates
---------------

Once you have upgraded your integration template to the latest version the previous Live template version will be tagged as Deprecated, being locked for editing.

![](./images/Integration-Template-Releases.png)

This allows you to keep a trail of your integration development progress, so you can see what you we previously doing, while also being able to go back by creating a copy of the deprecated template and promoting it to Live.





