# **ITSM APAC DEMO**
By Alvin Ong

This Bootstrapper allows you to run the following demo scenarios:
- Request Management
- Incident Management
- Problem Management
- Change Management

# **Pre-Demo Setup Steps PLEASE READ**
1. Please note the form IDs for IT Incidents, IT Request and Change Request Form. You can do so by going to the help center, log in as a end user. Click on submit a request and select each of the forms. For eg. "ticket_form_id=360000731751"

2. Go to the guide admin page and view the Chain Frost Theme.

3. Click "Edit Code"

4. Click on homepage_hbs and edit the form ID on line 40 "Need help?", 43 "Requesting something?" and 46 "Submitting change?". 

5. Please do the same for line 49 to link the "Knowledge" button directly to the FAQ and Announcement KB Category.

6. The "submit" button on the service catalog pages are linked directly to the instance. So please change the Zendesk instance domain and the include the form ID. 

```
<button onclick=\"window.location.href='https://[CHANGE TO YOUR OWN DOMAIN].zendesk.com/hc/en-us/requests/new?ticket_form_id=[INCLUDE THE FORM ID FOR THE SERVICE CATALOG FORM]'\">Submit Request</button>
```

7. Click on the Approvals Configuration app on the main navigation bar on the left in Zendesk and fill in **only email addresses** for each service request type and task type so that the approvals and task will be assigned. 

8. While on the Approvals Configuration App, you would also need to select the correct form and form field like the screenshot below:
![Image of Config](https://i.ibb.co/Ns5WcFb/11111.png)

# **Additional Info**

**Users created for the demo:**

- John Tan ECAB (ECAB Member)
- Peter Chan ECAB (ECAB Member)
- Chris Lim C Staff (C Staff)
- Prince Approver and Fulfiller (Default Approver and Fulfiller)

**To Add Service Catalog Items**

1. Create the Knowledge article and publish it. You could copy and paste the existing articles and replace the images.

2. To add icons onto the Service Catalog page in Zendesk, you would need to edit the code of the help center. Click edit code of the "Chain Frost Theme Builder" and add the following batch of code in "style.css".

```
.catalog-img-360040012212 {
  background:url($assets-msoffice-jpg);
}
```

3. Replace "360040012212" with the KB Article ID. You can find out the article ID by opening the article in the help center.

4. Replace "$assets-msoffice-jpg" with the asset image file. You will need to add new assets in the assets folder and refer to the text listed in the "CSS" textfield. You can find out this info by clicking on the asset in the assets folder.

# Request Management Flow 
1. Impersonate as an end user and go to the help center to request for a hardware or software.

**Note:** You may add more hardware or software that you feel that are relevant to the audience. Please refer to the above section for the steps to add new Service Catalog items.

2. Click on the top link to access the Service Catalog or click on the button on the front page "Requesting Something"

3. View the knowledge article and click on the button "Submit Request" at the bottom of the article. Fill in the form. For example: Subject: Requesting for a phone. Description: Current phone needs to be replaced.

4. Revert back to the agent's interface and walkthough on the landing page and the views.

5. Click on the ticket that is generated, and walkthrough on the form field and the apps side bar.

6. Optionally: Talk about the apps that are available on the marketplace that could provide more IT related functionality. Such as DevOps Integration or Remote desktop or Advanced Asset management.

7. Refer to the approvals side bar app and click approve. You could explain that this is all built using Sunshine which is available on the enterprise plan or otherwise they could also use an approval app that is available on the marketplace.

**Note:** If you have not change the approvals configuration app, the approver and assignees to the tasks created will be "aong@zendesk.com". Only the user "Alvin Ong" will be able to approve and complete tasks.

8. Once approved, there will be a fullfillment task created. You will be able to see the task link in the comments. The task  will be assigned to the IT team to procure/process the CI for the end user. Mentioned that there will be different SLAs tracking different type of tickets within Zendesk.

9. Click into the task link from the comments that will opened up a subticket. 

10. Click on the side bar app to set the task status to complete. 

11. Click back onto the original ticket and you could see the CI created and assigned to the User. This will be helpful as you could assign this CI to the ticket in the next demo flow - Incident Management.

# Incident Management Flow
1. Create and Incident ticket or have the end user submit a case through email/phone/web form depending on your prospect's requirement.

**Note:** If the end user is a C Staff, the ticket priority would be set to high and this will also meant that there is another SLA created specifically for C Staff's incidents and requests. You can find out if the end user is a C Staff by going to user profile in Zendesk and look for the Employee Status field. 

2. Once the case has submitted, revert back to the agent's interface to work on the ticket.

3. Using the CMDB 360 App, we can find out which CI is the end user refering and assign it to the ticket. Click assign on the CI that is affected and it would be moved to the "Related CI" section.

**Note:** You could also create a CI directly in this step instead of assigning. Fill in the CI Type and Model and click assign.

4. Explain the use of macros and mentioned that to the prospects that the agent have found out they noticed a surge of cases that seem related. Create another ticket and use the "Incident" macro to upgrade this to a problem ticket, and explain the use of relating the incidents to the problem ticket.

# Problem Management Flow
1. In the problem ticket view, explain the use of the Knowledge capture app.

2. Click back onto the Incident ticket and link this problem ticket in the problem ticket field. Explain the relationship and the advantages on such feature.

3. Using the problem macros and the Knowledge Capture App, the agent could easily link Workaround, Known errors and Root cause related articles to the ticket.

**Note:** You will need to use the problem macro and add the link via the Knowledge Capture App.

# Change Management Flow
1. When a change is required to implement a workaround due to the problem ticket, the agent could create a ticket under the change ticket form. Explain that the type of changes that the agent could use for a change management process. Standard changes are changes that does not need approvals, while normal and emergency changes would require approval.

2. Assign a CI to the change ticket and use the user "Prince". For eg. The ticket could be about patching a server for the latest security update and therefore you could create a Server CI before you start this demo. You could add any other CI directly from the CMDB 360 app.

3. Have the agent create a normal change ticket and assign the CI to the ticket.

4. Refresh the side bar app to see the approvals and approve the change ticket. Mentioned that multiple levels of approval could also be setup if it is required.

5. Optionally: You could impersonate as another user to approve the change request if the requester is not the approver as configued in the approvals configuration app.

6. Once approved, there will be two tasks created within the comments. A review task and an implement task

7. Optionally: Complete each of this task to close off the change request. Also remind them that there are SLAs for each ticket that is created to measure efficiency and performance.

8. Optionally: Explain the use of the ECAB macro to add the ECAB members to this change ticket as folleers if it is an emergency change for visibility. Mention that we could use business rules such as triggers or automations to shorten any other manual processes or integrate with other systems to form a complete change process.

# TO DO
- [ ] Incorporate HR Flow
- [ ] Help Center Updates
- [ ] ITSM Explore Dashboard

