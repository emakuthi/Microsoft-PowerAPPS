# Deployment Guide

  

  

## Prerequisites

  

- Microsoft 365 license

- Power Apps license

- Power Automate license

- A valid SharePoint Online license and permission to create lists and store dataa

- A copy of Safaricom App zip package.
  

**Step 1. Create an Safaricom admin group in Microsoft Teams**

Please ignore steps 1-5 below if you already have a team of admins and continue from step 6. Otherwise, please follow the steps below:

1. Open the Teams application on your desktop or on the web, navigate to [https://teams.microsoft.com](https://teams.microsoft.com)

  

2. Click on the **Teams** tab in the left-hand side menu

  

3. Click on **Join or Create Team**, then select **Create team**


  

4. Select **Build your team from scratch** > Select **Private** .
  

5. Provide your Team name(as Safaricom recommended) and description as appropriate to your business, then click **Next**
6. After that a popup will open where you need to add members in your created team. Add all the members and then close the popup.
7. Confirm if a new team is created successfully. 

  

8. Next to the team name, click on the ellipses (“…”) and select “Get link to team”

![GetLinkToTeam](/Wiki/images/GetLinkToTeam.png)

  

9. Click on “Copy” to copy the link to clipboard

![CopyTeamLink](/Wiki/images/CopyTeamLink.png)

10. Get the groupID query string value as shown below:

  
  

![Get group ID](/Wiki/images/groupId.png)

  

11. Copy the groupId as it will be used in further steps.
  

**Step 2. Create the SharePoint site**

Please ignore this step if you already have a SharePoint site intended to use for Safaricom application.
-   Login to SharePoint (i.e  [https://tenant-name.sharepoint.com/](https://tenant-name.sharepoint.com/)  ) and click on Create site at the top left corner of the page..
- Select Team Site in Popup Window.
- Enter Site Name(Safaricom) then select Next.
- Now you will be navigated to SharePoint site .
- Keep the Safaricom SharePoint site address handy as it will be needed multiple times in further steps.
  
**Step 3. Create the SharePoint Lists**

1. Sign in to Power Automate [Click Here](https://flow.microsoft.com/en-us/).
	- Select **My Flows** in the left panel, click on Import
	- Upload **Create Safaricom SharePoint Lists.zip** from the package provided.
	- Once imported, click on “Edit”.

  

  

![Create sharepoint list](/Wiki/images/ImportSharePointFlow.png)

  

2. Import package page will open. In related resources column ,Click on select during import.

  

  

- If connections are already available click on any of them and Save it and select Import.

  

![Import package](/Wiki/images/AddSharePointConnection.png)

  

-  If there are no connectons in the right rail click on *Create New*, it will redirect to a new page where you can add a new connection by searching for SharePoint and logging in

  

![AddSharePointConnectionFlow](/Wiki/images/AddSharePointConnectionFlow.png)

  

-  Now connection will be added and you can Navigate to previous flow tab and select the connection in right rail.

  

4. Once the flow is succesfully imported. Click on Open flow. 


  

5. Click on Test Icon in the right top corner. And then select I’ll perform the trigger action. Click on Save&Test.
	-  You will then get a popup to enter the TeamSharePoint URL , Enter the Safaricom Team Site Url).
	-  Then click on Run Flow, Now click on done.


  

6. Once the flow is successful, You will get the below screen.

  

![Flow run success](/Wiki/images/SharePointflowSuccesful.png)

  

  

7. The below 6 lists will be created in Safaricom Site:

  

  

	**a.** SwapRequestDetails

	**b.** ParkingRequestDetails

	**c.** EmployeeDetailsTemplate

	**d.** SecurityUpdateStatusTable

	**e.** SecurityEntryListTable

	**f.** ParkingDetailsTemplate

8. Follow above steps and import *Data Insertion Flow* from Microsoft Flows folder in package. Once the flow is imported, open OneDrive in new tab .
Note : This flow is to add parking details excel data to SharePoint list.
	- For this you need to upload EmployeeDetailsTemplate& ParkingDetailsTemplate excel 
	- EmployeeDetailsTemplate should contain three columns with jobGroup and OnBehalfType 
	- Ignore the Title field it can be anything
	- ParkingDetailsTemplate  should contain columns as shown in screenshot.

	![ParkingDetailsTemplate](/Wiki/images/ParkingDetailsTemplate.png)
     
	- Please refer the sample excel provided in package 
	- Go to one drive and upload below two files

		1. Parking details template

		2. Employee details template

		3. Now Go to *Data Insertion Flow* tab and select OneDrive uploaded files as mentioned in comments in the flow. Now, follow step 3.5.
  

9. Navigate to Safaricom Site. Click on the Site Contents in the left hand side then select**Parking Request Detail** list

  

  

	**a.** Click on the settings icon at the top right-hand corner

  

  

	**b.** Go to List settings

  

  

	**c.** Click on “Advanced Settings”

  

  

	**d.** Give below permissions at the Item-level

  

  

![Legal Permission](/Wiki/images/ListSettings.png)

  


  

**Step 3: Import package in Power Apps for Safaricom and Safaricom Security using the zip file**

  

  

1. Navigate to the Power Apps platform (https://make.powerapps.com/)

  

2. Click on **Apps** in the left side pane and click on **Import canvas app.**

  

3. Import the **Safaricom.zip** from package.

  

4. You will be automatically redirected to the details page

  

5. In the package details page, click on **Select during import** for SharePoint connection in **import setup** column

  

6. If you do not find any existing connections, click on **Create new** button in the popup. The page will open in a new browser tab

  

7. Click on **Create a connection** button

  

8. You will be able to see the list of available connections. Click on **+** for SharePoint connection

  

9. Check **Connect directly (Cloud services)** option in the popup and click on **Create** button

  

10. Login to confirm the connection setup correctly

  

11. Navigate back to the **import package** tab. Once the connection is created, you will be able to see the connection in the import setup dialog

  

12. If you are not able to see the SharePoint connection, click on **Refresh List** button in the dialog

  

13. Click on the connection name to select it and then click on **Save**

  

14. You will be able to see that SharePoint is connected to your tenant

  

15. Click on the **Import** button at the bottom of the page


  

16. Repeat the steps from step 5 for all connections for  **Safaricom Security.zip**.

  

  

**Step 4: Edit Data source**

  

1. Click on **Open app** link when the zip package is successfully imported. You will be redirected to the PowerApps portal

  

2. Click on **Open** menu at the left side of the screen -> **PowerApps** -> **Safaricom/Safaricom Security** app which you have imported

  

3. The app will request your permission to use all the listed data connections

  

4. Once the app opens,**Only for the Safaricom App** - Click on 2nd icon in left hand pane and select App.Then change the highlighted part with Teams group id that you have created at the beginning.

  

![Group ID](/Wiki/images/AddGroupId.png)

  

5. In the horizontal menu, click on **View** and select **Data sources**

  

6. Delete below existing SharePoint connections

	- Swap Request Detail

	- Parking Request Detail

	- Employee Details Template

	- Security Update status table

	- Security Entry List Table

	- Parking details template

  

7. Search for SharePoint and select it

  

8. Enter the newly created SharePoint URL in the pop-up window

  

9. Choose below lists and select connect

	- Swap Request Detail

	- Parking Request Detail

	- Employee Details Template

	- Security Update status table

	- Security Entry List Table

	- Parking details template

  

  

10. Follow step 4 and step 5 above, for importing the Safaricom security package **SafaricomSecurity.zip**
11. Now click on **File** menu, select Save.
12. For the Safarciom App, In the File menu , Click on Settings
13. Select Name+Icon, the click on EditApp Name in the right window.
14. You will navigated to new tab, which shows the details of app.
15. Please note down the App Id from the details as it would be used in flows.

![AppDetails](/Wiki/images/AppDetails.png)

  

  

**Step 5: Edit Flow Data Source**


Note : When a PowerApps package is imported, all the related flows would be imported which needs to be modified as per new SharePoint site, Teams channel.

  

The flows that would need to be modified are :

  

- ParkingReleasedNotification

  

- ApprovedRequestFlow

  

- RenewParkingNotification

  

- SwapAdminFlow

  

- NewRequestNotification

- SwapFlow

  

1. Open Power Automate (https://flow.microsoft.com/en-us/)

  

  

2. Click on MyFlows in left panel.Click on import, import **Check Date Flow** from Flows folder from the package provided. click on **Open flow**

	Note : Comments has been provided in every step in flow for your reference as below. Please change the steps accordingly wherever you find comments in flows. Please have look at the comments(highlighted parts) in below screenshot.
	
	-  In **Get items -** Change the site address to the new SharePoint site which has been created in Step - 2 (Safaricom sharepoint site URL) and change the list name to **ParkingRequestDetails**. 


![ReferComments](/Wiki/images/ReferComments.png)




![CheckDateFlow](/Wiki/images/CheckDateFlow.png)

  

3. Click on MyFlows in left panel. Select the flow **New Request Notification** connected to Power Apps. click on **Edit icon.**

	- In the second step, Click on App Id and provide the AppId that you have noted from App Details.
	- In the **Post your own adaptive card as the Flow bot to a channel** select the team name which you have created in step - 1 (admin group name).
	- Click on Save in the right side.

![AppId](/Wiki/images/AppId.png)
	
![SelectAdminGroup](/Wiki/images/SelectAdminGroup.png)
	
  

4. Follow above step for **Renew Parking Notification** 

  

5. Click on MyFlows in left panel. Select the flow **SwapAdminFlow** connected to Power Apps. click on **Edit icon.**
	- Change the App Id.
	- For all the steps with SharePoint icon, change all the site addresses to Safaicom site address, List Name as the name mentioned in comment.
	- Save the flow.
6. Repeat above step for SwapFlow, ParkingReleasedNotification flows
  
  
  
  


**Step 6: Share Power App**

  

  

The admin would need to share the app to all individuals who will be using the app (this includes the admins and doctors).

  

  

1. Open the PowerApps user interface (https://make.powerapps.com/)

  

  

2. Go to the Apps menu in the left-hand side menu bar and you will be able to see the list of apps which have been imported

  

  

3. Click on the ellipses (3 dots) for your app, and click on **Share**

  

  

4. Enter the users with whom you want to share the app with, and click on **Share**

  

  

**Step 7: Adding Safaricom Power App to Microsoft Teams**

  

  

1. Navigate to Power Apps (https://make.powerapps.com/)

  

  

2. Click on the ellipses (3 dots) for your app, and click on **Add to Teams**

  

  

3. A compressed file (zip) will be downloaded to your Downloads directory in your browser

  

  

4. Open the Microsoft Teams desktop app, or web app by navigating to the link here ([https://teams.microsoft.com](https://teams.microsoft.com))

  

  

5. Go to the apps menu in the left hand side

  

  

6. Click on the option that reads: **Upload a custom app**

  

  

7. Upload the downloaded zip file

  

  

8. You should see the app.