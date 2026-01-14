
# CopilotAdoptionAgent

Copilot Adoption Agent – README Document 

Overview 
The Copilot Adoption Agent (1.1.0.3) is a packaged Copilot Studio solution designed to 
help organizations accelerate adoption of Copilot Chat and Microsoft 365 Copilot 
through automated, structured communication campaigns. 

This agent delivers a complete, ready-to-run 30-day email adoption program, sending 
users three targeted emails per week that progressively build Copilot skills at the Beginner, 
Intermediate, and Advanced levels. 

While the agent includes optional enablement guidance for administrators, its primary 
purpose is to automate adoption communications, not to manage licensing or 
provisioning. 

What This Agent Does:
• Automates delivery of a 30-day Copilot adoption email campaign.
• Sends 3 emails per week (Tuesday, Wednesday, Thursday at 10:00 AM Central 
Time).
• Sends emails from the authenticated user’s mailbox who is entering the request 
in the agent experience (author).
• Provides prewritten email templates for both Copilot Chat and Microsoft 365 
Copilot.
• Supports Beginner, Intermediate, and Advanced learning tracks.
• Includes test flows to validate environment configuration.
• Offers optional Q&A for user enablement and adoption recommendations.
leveraging the Enablement Guides for both products as the knowledge references. 

Included in This Solution 
Core Components 
• Copilot Studio Agent 
The conversational interface used to configure campaigns, select product type, 
choose skill level, and define the target audience. 
• Prebuilt Prompts & Logic 
All decision logic, branching, and campaign configuration steps required to run the 
adoption program. 
• Email Template Library 
Fully authored communication templates for: 
o Beginner 
o Intermediate 
o Advanced 
For both Copilot Chat and Microsoft 365 Copilot. 
Power Automate (Agent) Flows – 12 Total 
The solution includes 12 Power Automate flows, grouped into Test and Production sets. 
6 Test Flows (Environment Validation) 
These flows allow administrators to validate: 
• Email formatting and rendering 
• Template selection 
• Routing to the target distribution lists 
• Authentication of the sender’s personal mailbox 
• Variable timing logic for testing, with entering a delay in minutes to verify emails 
• Overall readiness before launching a live campaign 
6 Production Delivery Flows 
These flows execute the live 30-day campaign: 
• Deliver emails on Tuesday, Wednesday, Thursday at 10:00 AM Central. This initial 
delivery will start at the next planned window based on agent engagement.   
• Use the selected product (Copilot Chat or Microsoft 365 Copilot) 
• Use the selected skill level (Beginner, Intermediate, Advanced) 
• Send from the authenticated user’s mailbox 
• Reminder emails with instructions to track adoption progression  
• The individual Agent Flows can be reviewed at any time to see the progress of the 
delivery. 
Each production flow corresponds to a specific product + skill level combination, keeping 
campaigns isolated, predictable, and easy to manage. Multiple campaigns can be run at 
the same time.  All campaigns are independent of each other. 



Prerequisites & Required Roles 


 Environment Requirements 
• A Microsoft 365 tenant with Copilot Studio enabled 
• Access to a Dataverse environment (default or custom) 
• A user mailbox capable of sending outbound email (Microsoft 365 author’s account) 
Role Requirements 
To import and configure the solution, you must have one of the following roles for the target 
environment that the Copilot Adoption Agent will be ingested into: 
• Environment Admin 
• System Administrator 
• Copilot Studio Administrator 
• Power Platform Admin 
To send emails from the author’s account from the agent, the author must also: 
• Authentication of the Outlook connector to the connector resource (happens during 
ingestion). 
• Be licensed for Microsoft 365 Copilot. 
• Have permission to send to the target distribution list.


Importing the Copilot Adoption Agent into Copilot Studio 
1. Download the Solution Package 
Obtain the .zip solution file from this repository’s release or solution folder. 
2. Open Copilot Studio 
Navigate to: 
https://copilotstudio.microsoft.com 
3. Select Your Environment 
Choose the Dataverse environment where the agent should be installed. 
4. Import the Solution (Critical Advanced Settings Step) 
• Go to … on left panel, and select Solutions 
• Select Import solution 
• Upload the .zip file 
• When the import wizard appears, expand Advanced Settings 
• Uncheck the option: 
“Enable all workflows and connections included in the solution” 
***This step is critical. 
***Unchecking this box prevents the 12 Power Automate flows from activating before 
your mailbox authentication is confirmed. 
• Proceed with the import! 
5. Verify Connection Resources (Important) 
Once the solution appears in your Solutions list: 
1. Open the Copilot Adoption Agent solution. 
2. Select Connection Resources. 
3. Locate the connection named cr_Outlook. 
4. Ensure author’s account is bound to this connection resource. 
It should bind automatically, but verifying this ensures the agent will send emails from your 
mailbox without errors. 
6. Open the Copilot Adoption Agent 
Once the installation is completed, the author can visit Inside the agent, the author will 
work with the chat interface to: 
• Select the product (Copilot Chat or Microsoft 365 Copilot) 
• Select the skill level (Beginner, Intermediate, Advanced) 
• Provide the target distribution list 
• Confirm the campaign schedule 
7. Run Test Flows (Recommended) 
Use the six included test flows to validate: 
• Email formatting 
• Routing 
• Permissions 
• Template accuracy 
8. Activate the Production Campaign 
Once validated, start the production flow for your selected product and skill level. 
Emails will automatically be sent on the defined cadence for 30 days from author’s 
mailbox. 
**While you can choose to formally publish the Copilot Adoption Agent following Microsoft 
processes (Key concepts - Publish and deploy your agent - Microsoft Copilot Studio | 
Microsoft Learn), this is technically not required.  If the person ingesting the agent will be 
the same one operating it, then you can leverage the Test experience in the Agent while in 
Copilot Studio to issue commands. 


Operating the Copilot Adoption Agent 
The agent is designed to be simple and command-driven. There are two primary 
commands you will use: 
1. TEST start email scheduler 
Use this command when you want to run the test version of the campaign. 
This mode allows you to: 
• Validate email formatting 
• Confirm routing to the distribution list 
• Test your mailbox authentication 
• Control the delay between emails (in minutes) 
o Example: send test emails every 5 minutes instead of waiting days 
This is the recommended first step before running a production campaign. 
2. start email scheduler 
This command launches the full production 30-day campaign, using: 
• The selected product (Copilot Chat or Microsoft 365 Copilot) 
• The selected skill level (Beginner, Intermediate, Advanced) 
• The configured distribution list (recommended) 
o Individual emails addresses can be used, but more than one requires a semi
colon (;) used between addresses to meet Outlook structure. 
• The fixed schedule of Tue/Wed/Thu at 10:00 AM Central 
Once started, the campaign runs automatically for 30 days. 
3. Ask questions or request recommendations 
Beyond campaign execution, the agent can also answer: 
• Copilot adoption best practices 
• Tips for onboarding users 
• Guidance on communication strategy 
• General Copilot enablement questions 
This makes the agent useful both as a campaign engine and an adoption advisor. 
Email Delivery Notes 
• Emails are sent from the authenticated author ’s mailbox 
• Campaigns run independently for each product/skill level 
• Multiple campaigns may run in parallel 
• Timing is fixed to Tues/Wed/Thurs at 10:00 AM Central Time 
Customization Options 
Given you have an unmanaged Agent, Admins may optionally customize: 
• Email html templates (within Agent Flows, manually) 
• Timing and cadence (within Agent Flow, manually) 
• Branding or formatting (requires internet accessible storage and html editing) 
• Additional enablement content 

Support & Troubleshooting 
If emails fail to send: 
• Verify Outlook connector is connected (connectors can become unconnected over 
time with lack of usage) 
• Ensure the distribution list accepts automated or bulk senders 
• Validate that test flows successfully 
