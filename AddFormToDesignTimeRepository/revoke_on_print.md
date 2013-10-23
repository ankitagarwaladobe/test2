##Rights Management - Revoke On Print

The Revoke On Print sample describes how to revoke a policy-protected document as soon as it is printed by using a long-lived process.  
This sample consists of two processes, the Apply Policy process and the Revoke On Print process.  
The Apply Policy process applies a test policy to one PDF document. Then the Revoke On Print process revokes the policy once the document is printed.

**Note**: Rights Management module must be installed.

Files needed for the sample
---------------------------

**Adobe-Samples-Service-RightsManagement.lca** -- `The archive used for deploying the sample`  
**collateral/SampleToSign.pdf**	-- `Input PDF document with policy applied`

Deploying the sample
--------------------

**Tip:** To deploy multiple samples, use the Samples Deploy Utility.

**Note:** These instructions assume that ADEP-Document Services/LiveCycle ES4 is installed on the C: drive on Microsoft Windows.  
If you have installed to a different location, substitute the directory where you installed Document Services/LiveCycle ES4.

* Check the following folder in the file system on the server where Document Services/LiveCycle is installed, if it exists, delete it before proceeding

**Windows** -- `C:\tmp\LCSamples\WatchedFolder\RightsManagement\ApplyPolicy`
**UNIX** -- `/tmp/LCSamples/WatchedFolder/RightsManagement/ApplyPolicy`

* Log in to Administration Console.
* Click **Services > Applications and Services > Application Management**.
* Click the **LiveCycle Applications** tab and click **Import**.
* Click **Browse** to locate the sample archive (LCA) file **Adobe-Samples-Service-RightsManagement.lca**, and then click **Preview**.
* Select **Deploy** assets to runtime when import is complete and click **Import**.

Configuring the sample
----------------------

**Note**: Before configuring and running this sample, it is necessary to deploy and run the Sample Setup Utility.

**Configure SSL:**

To configure SSL for Turnkey installation, see Installing and Deploying LiveCycle ES4 Using Turnkey or the ADEP Turnkey document.  
To configure SSL for other servers, follow the instructions detailed in the LiveCycle Administration Console Help or the ADEP Administration Console Help.  
This step is only necessary if SSL was not installed during the installation process.

**Note**: If you are using the turnkey install, restart JBoss in order for the SSL configuration to take effect.

**Configure Rights Management:**

**Create a policy**

* Log in to the **Administration Console** (http://hostname:port/adminui) with the Super Administrator.
* Navigate to **Home > Services > Rights Management > Policies > Policy Sets**, and click **Global Policy Set**.
* Click **Policies** tab and then click **New** button to create a policy.
* Enter **RMSampleTestPolicy** as the policy name and click **Save**. The page returns to the **Global Policy Set** page.
* To enable the newly created policy, check the checkbox **RMSampleTestPolicy** and click **Enable**.

Configure the Rights Management Base URL
----------------------------------------

* Log in to **Administration Console** (http://hostname:port/adminui) with super administrator.
* Click **Services > Rights Management > Configuration > Server Configuration**.
* Configure Base URL of the settings. The base URL must contain the fully qualified hostname of Document/LiveCycle server and port.  
For example, https://[fully_qualified_hostname]:[port_number], https://lcserver.mycompany.com:8443.
* Leave all other properties of the setting as default value, and click **OK**.

Enable EventHandler
-------------------

The RightsManagement Event invokes the RevokeOnPrint process. By default, the event is not enabled. To enable the event:

* Log in to Administration Console (http://hostname:port/adminui) with super administrator.
* Click **Services > Rights Management > Configuration > Manual Configuration**.
* Click **Export**, and specify a location to save the configuration XML file.
* Open the configuration XML file exported with a text editor. In the editor, locate the **<node name="SDK">** element,
```
<preferences EXTERNAL_XML_VERSION="1.0"> 
     <root type="system"> 
         <node name="Adobe"> 
             <node name="LiveCycle"> 
                 <node name="Config"> 
                     <node name="PolicyServer">
                         <node name="SDK">
```

Modify the entry element that has the key attribute with the value EventHandlersEnabled. Set the value attribute to a value of true.
<entry key="EventHandlersEnabled" value="true" />

Save the file and return to the Manual Configuration page of Administration Console to import the configuration file. Click Browse and specify the configuration file that you modified. Click Import and then click OK.
Install the server certificate from web browser:

To allow Adobe Acrobat/Adobe Reader to accept the server SSL certificate from the Document/LiveCycle server, install the certificate into the browser (Microsoft Internet Explorer):

On the system where the Document/LiveCycle server resides, open URL https://<fully_qualified_hostname>:<port>. Set the URL to be the same as the Base URL you set in step Configure the Rights Management Base URL. A Certificate Error page displays in the browser, choose "Continue to this website (not recommended)."
From the top of the browser, click Security Report (with message "Certificate Error") next to address bar, then click View certificates, a Certificate window displays.
In Certificate window, click Install Certificate to launch Certificate Import wizard.
In the Certificate Import wizard, click Next in the Welcome page, choose Place all certificates in the following store in Certificate Store page, click Browse.... From the Select Certificate Store window choose Trusted Root Certification Authorities then click OK to close the window and return to Certificate Import wizard window.
Click Next, then click Finish in Completing page.
If you get a Security Warning dialog pops up, choose Yes.
You can see a message box "The import was successful" once the import finishes. Click OK in Certificate window.
To verify the installation, open the Base URL from a new browser, the page can be opened without any security alert.
Configure Policy

Log in to Workbench.
If Samples - Rights Management does not show in the Applications view, click File > Get Application.... Choose Samples - Rights Management > Samples - Rights Management/1.0 from the application list to import the application to Workbench.
In the Applications view, click Samples - Rights Management > Samples - Rights Management/1.0> Processes > Apply Policy. To check out the process, right-click Apply Policy and select Check Out. To edit the process, right-click Apply Policy and select Open.
Click the activity Protect Document. In Process Properties > Input area, ensure that the Policy set name is Global Policy Set and Policy name is RMSampleTestPolicy.
To save the process, select File > Save.
In the Applications view of Workbench, click Samples - Rights Management > Samples - Rights Management/1.0. To check in the application, right-click Samples - Rights Management/1.0and select Check In. To deploy the process, right-click Samples - Rights Management/1.0and select Deploy.
Configure Watched Folder

This step is optional if you do not want to change the default watched folder path.

The path of the WatchedFolder startpoint is C:\tmp\LCSamples\WatchedFolder\RightsManagement\ApplyPolicy by default for Windows, and /tmp/LCSamples/WatchedFolder/RightsManagement/ApplyPolicy for Unix. If you want to change this path, complete the following steps:

Log in to Workbench.
If Samples - Rights Management does not show in the Applications view, click File > Get Application.... Choose Samples - Rights Management > Samples - Rights Management/1.0 from the application list to import the application to Workbench.
In the Applications view, click Samples - Rights Management > Samples - Rights Management/1.0> Processes > Apply Policy. To check out the process, right-click Apply Policy and select Check Out. To edit the process, right-click Apply Policy and select Open.
Click the startpoint Apply Policy - startpoint, and in Process Properties > General > Path, you can enter (for example):

Windows	D:\temp\LCSamples\WatchedFolder\RightsManagement\ApplyPolicy
UNIX	/home/yourUserName/LCSamples/WatchedFolder/RightsManagement/ApplyPolicy
To save the process, select File > Save.
In the Applications view of Workbench, click Samples - Rights Management > Samples - Rights Management/1.0. To check in the application, right-click Samples - Rights Management/1.0and select Check In. To deploy the process, right-click Samples - Rights Management/1.0and select Deploy.
Running the sample

Copy the PDF file SampleToSign.pdf to the watched folder's input directory, by default it is C:\tmp\LCSamples\WatchedFolder\RightsManagement\ApplyPolicy\input for Windows and /tmp/LCSamples/WatchedFolder/RightsManagement/ApplyPolicy/input for Unix. The sample PDF is located in the folder collateral within the ZIP file Adobe-Samples-Service-RightsManagement.zip.
After a while, the output PDF file SampleToSign.pdf is saved to the watched folder's result directory, by default is C:\tmp\LCSamples\WatchedFolder\RightsManagement\ApplyPolicy\result\yyyy\mm\dd\ for Windows and /tmp/LCSamples/WatchedFolder/RightsManagement/ApplyPolicy/result/yyyy/mm/dd/ for Unix.
Open the output PDF file with Adobe Acrobat or Adobe Reader. A Security Warning dialog displays indicating that the document has a policy applied and now is protected and connects to the Document/LiveCycle server.


Note: If you are using Acrobat X to open the PDF file, you will see login dialog directly without clicking Allow in the dialog above.

Click Allow to log in. Enter the username and password as username/password=atanaka/password (for example. set atanaka as the publisher in the process), click OK.


The dialog box about viewing secure documents offline displays. Click Yes to open the PDF.
Troubleshooting: If you get error that relates to http protocol, which means the SSL or Rights Management is not setup correctly. See the SSL document or Rights Management document to configure them correctly.



Select File > Print from the Adobe Acrobat/Adobe Reader menu to print this document. Print either a hard copy or print via virtual printer such as Adobe PDF Printer.
Close the output document and then reopen it. A dialog indicating that that the document is terminated and no longer valid displays. When the document is printed, the revoke process event is invoked to revoke the license on the document.


Next steps

This process catches the event of printing the document, and then revokes the license on the document. To try other events, see the LiveCycle Workbench Help or the ADEP Workbench Help for more details.

Legal disclaimer

Any references to company names, company logos and user names in sample material or sample forms included in this documentation and/or software are for demonstration purposes only and are not intended to refer to any actual organization or persons.

Service Sample - Document Services/LiveCycle ES4 Rights Management - Revoke on Print - 08/04/2011 10:52 PM 
August 2011
