Rights Management - Create From Template And Apply Policy
---------------------------------------------------------

Overview of the sample
----------------------

This sample demonstrates how to create a policy from a preexisting policy within a short-lived process, apply the newly-created policy to a PDF document within the same process, and create a sample client that calls the service container and writes the resulting secured PDF file.

[Note:]() You must ensure the Rights Management component is installed.


Files needed for the sample
---------------------------

The following files are required to run this sample.

* [Adobe-Samples-Service-RightsManagement.lca]() --	`The LiveCycle ES4 archive used for deploying the sample`
* [SampleToSign.pdf]() -- `Testing file, can be found in the collateral directory of the source ZIP file`

Deploying the sample
--------------------

[Tip:]() To deploy multiple samples, use the **Samples Deploy Utility**.

[Note:]() These instructions assume that LiveCycle ES4 is installed on the C: drive on Microsoft Windows, if you have installed to a different location, substitute the directory where you installed LiveCycle ES4.

* Check the following folder in the file system on the server where LiveCycle ES4 is installed, if it exists, delete it before proceeding  

**Windows**	C:\tmp\LCSamples\WatchedFolder\RightsManagement\CreateFromTemplateAndApplyPolicy  
**UNIX**	/tmp/LCSamples/WatchedFolder/RightsManagement/CreateFromTemplateAndApplyPolicy

* Log in to LiveCycle Administration Console .
* Click **Services > Applications and Services > Application Management.**
* Click the **LiveCycle Applications** tab and click **Import**.
* Click **Browse** to locate the sample LiveCycle ES4 archive (LCA) file **Adobe-Samples-Service-RightsManagement.lca**, and then click **Preview**.
* Select **Deploy assets to runtime** when import is complete and click **Import**.

Configuring the sample
----------------------

[Note:]() Before configuring and running this sample, it is necessary to deploy and run the Sample Setup Utility.

Configure SSL:
-------------

If SSL is installed during installation, ignore this section. To configure SSL follow the instructions detailed in the LiveCycle Administration Console Help.

**Configure Rights Management:**

* Log in to LiveCycle Administration Console (http://hostname:port/adminui).
* Click **Services > LiveCycle Rights Management ES4 > Configuration > Server Configuration**.
* Configure Base URL of the settings, the base url should contain the fully qualified hostname of LiveCycle server and port ,  
like https://[fully_qualified_hostname]:[port_number], For example, https://lcserver.mycompany.com:8443.
* Leave all other properties of the setting as default value, and click OK to finish the server configuration settings.
* Click **LiveCycle Rights Management ES4 > Policies**, click the tab **Policy Sets**.
* Click **Global Policy Set**, and then click tab **Policies**, enable **“Restrict to All Principals”** policy manually.

**Install the server certificate from web browser:**

The server certificate can be installed using a web browser on the system where LiveCycle ES4 server is located, the steps may vary on different web browsers. Below is an example for Internet Explorer 8 on Windows,

* On the system where LiveCycle ES4 is installed, open URL http://<fully_qualified_hostname>:<port>, the URL should be the same as the Base URL you set as described in above step,  
a Certificate Error page should be displayed in the browser, choose "Continue to this website (not recommended)."
* Click **Security Report** (with message "Certificate Error") next to address bar, then click **View certificates**, a Certificate window displays.
* Click **Install Certificate** to launch Certificate Import Wizard.
* Click **Next** in the Welcome page, choose **Place all certificates** in the following store in Certificate Store page, click **Browse**..., from Select Certificate Store window choose **Trusted Root Certification Authorities** then click **OK** to close it and go back to Certificate Import Wizard window.
* Click **Next** , then click **Finish** in Completing page.
* If a Security Warning dialog displays, choose Yes.  
You can see a message box "The import was successful" once the import is finished. Click OK in Certificate window.

To verify the installation, open the Base URL from a new browser, the page can be opened without any security alert.

**Configure Watched Folder**

This step is optional if you don't want to change the default watched folder path.

The path of the WatchedFolder startpoint is-  
**C:\tmp\LCSamples\WatchedFolder\RightsManagement\CreateFromTemplateAndApplyPolicy** by default for Windows  
and **/tmp/LCSamples/WatchedFolder/RightsManagement/CreateFromTemplateAndApplyPolicy** for Unix.  
If you want to change this path, complete the following steps:

* Log in to Workbench ES4.
* If **Samples - Rights Management** does not show in the **Applications** view,  
click **File > Get Application**..., and choose **Samples - Rights Management > Samples - Rights Management/1.0** from the application list to import the application to Workbench ES4.
* In the Applications view, click **Samples - Rights Management > Samples - Rights Management/1.0> Processes >Create From Template And Apply Policy**.  
To check out the process, right-click **Create From Template And Apply Policy** and select **Check Out**.  
To edit the process, right-click **Create From Template And Apply Policy** and select **Open**.
* Click the startpoint **Create From Template And Apply Policy - startpoint**, and in **Process Properties > General > Path**,  
you can enter (for example):  
**Windows**	D:\temp\LCSamples\WatchedFolder\RightsManagement\CreateFromTemplateAndApplyPolicy  
**UNIX**	/home/yourUserName/LCSamples/WatchedFolder/RightsManagement/CreateFromTemplateAndApplyPolicy  
* To save the process, select **File > Save**.  
* In the Applications view of Workbench ES4, click **Samples - Rights Management > Samples - Rights Management/1.0**.  
To check in the application, right-click **Samples - Rights Management/1.0** and select **Check In*.  
To deploy the process, right-click **Samples - Rights Management/1.0** and select **Deploy**.

Running the sample
------------------

* Copy the PDF SampleToSign.pdf to the watched folder's input directory,  
by default is C:\tmp\LCSamples\WatchedFolder\RightsManagement\CreateFromTemplateAndApplyPolicy\input for Windows  
and /tmp/LCSamples/WatchedFolder/RightsManagement/CreateFromTemplateAndApplyPolicy/input for Unix.
The sample PDF is located in the folder collateral within the ZIP file **Adobe-Samples-Service-RightsManagement.zip**.

* After a while, the output PDF file SampleToSign.pdf is saved to the watched folder's result directory,  
by default is C:\tmp\LCSamples\WatchedFolder\RightsManagement\CreateFromTemplateAndApplyPolicy\result\yyyy\mm\dd\ for Windows  
and /tmp/LCSamples/WatchedFolder/RightsManagement/CreateFromTemplateAndApplyPolicy/result/yyyy/mm/dd/ for Unix.
* Open the output PDF file, the dialog box Security Warning will popup, click Allow to step into dialog box Log In, enter the username and password using the username/password=atanaka/password (or other users within the domains of LiveCycle), click OK, the dialog box View secure documents offline? will pop up, click Yes,
then the PDF file will be opened.  
* [Troubleshooting:]() if you get error that relates to http protocol, which means the SSL or Rights Management is not setup correctly, please refer to SSL document or Rights Management document to configure them correctly.

Next steps

Try making the following changes to the process:

Use a different form type.  
Use a different policy for the document.

Legal disclaimer
----------------

Any references to company names, company logos and user names in sample material or sample forms included in this documentation and/or software are for demonstration purposes only and are not intended to refer to any actual organization or persons.

Service Sample - LiveCycle ES4 - Rights Management - Create from Template and Apply Policy - 01/11/2010 1:44 PM  
LiveCycle ES4 - January 2010 
