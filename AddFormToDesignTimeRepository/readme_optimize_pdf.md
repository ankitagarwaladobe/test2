#PDF Generator - Optimize PDF

Overview of the sample
----------------------

This sample accepts a PDF file and optimizes it. The optimization settings can be configured through a file type setting or through a configuration file.  

##Files needed for the sample

The following files are required to run this sample.

**Adobe-Samples-Service-PDFGenerator.lca** -- `The archive used for deploying the sample`  
**Testing files** -- `Testing files of some most used file types provided to test the sample, can be found in the collateral directory of the source zip file.`

##Deploying the sample

**Tip**: To deploy multiple samples, use the Samples Deploy Utility.

**Note**: These instructions assume that Document Services/LiveCycle ES4 is installed on the C: drive on Microsoft Windows. If you have installed to a different location, substitute the directory where you installed Document Services/LiveCycle ES4.

* Check to see if the following folders exist on the server when Document Services/LiveCycle is install, if they do exist, delete them before proceeding.  
  **Windows**	C:\tmp\LCSamples\WatchedFolder\ConvertAllFileTypesToPDF
  **Unix**	/tmp/LCSamples/WatchedFolder/ConvertAllFileTypesToPDF
* Log in to Administration Console (http://[hostname]:[port]/adminui).
* Click **Services > Applications and Services > Application Management.**
* Click the **LiveCycle Applications** tab and click **Import.**
* Click **Browse** to locate the sample archive (LCA) file **Adobe-Samples-Service-PDFGenerator.lca**, and then click **Preview**.
* Select **Deploy assets to runtime when import is complete** and click **Import.**

##Configuring the sample

**Create File Type Settings**

* Log in to Administration Console.
* Click **Home > Services > PDF Generator > File Type Settings.**
* Click **New**, and then click **PDF Optimizer**. In the **Discard Objects** area, select **Discard bookmarks**.  
  In the **Discard User Data** area, select **Discard all comments, forms and multimedia**. In the **Clean Up** area, select **Discard invalid links**.
* Click **Save**, enter **"PDF Optimize Sample"** as the new file type setting's name and click **OK**.
* Log in to Workbench.
* If Samples – **PDF Generator** does not show in the application view, click **File > Get Application…. Choose Samples - PDF Generator > Samples – PDF Generator/1.0** from the application list.
* In the Applications view, click **Samples – PDF Generator > Samples – PDF Generator/1.0 > Processes >OptimizePDF**. To check out the process, right-click **OptimizePDF** and select **Check Out**, to edit the process, right-click **OptimizePDF** and select **Open**.
* Double-click the **Optimize PDF** activity to open its properties sheet.
* In the Process Properties view, open **Input > Filetype setting**, select **PDF Optimize Sample** from the drop-list box.
* To save the process, select **File > Save.**
* In the Applications view, click **Samples - PDF Generator > Samples - PDF Generator/1.0.**  
  To check in the application, right-click **Samples - PDF Generator/1.0** and select **Check In**, to deploy the application, right-click **Samples - PDF Generator/1.0** and select **Deploy**.

**Configure Windows 2008 x64 Enterprise Server to run PDF Generator**

To run this sample successfully, ensure that PDF Generator is enabled. The following steps are required to enable PDF Generator on a Windows 2008 x64 Enterprise Server. If PDF Generator is configured during Document Services/LiveCycle installation, skip this step. Check with your system administrator to find out whether PDF Generator is configured.

* Create at least two users with Administrative privileges in the Windows operating system, for example, "PDFGUser1" and "PDFGUser2".
* Disable **UAC** for these users: to turn UAC off, go to **Control Panel > User Accounts > Turn User Account Control on or off**. Deselect **Use User Account Control (UAC) to help protect your computer** and click **OK**. Restart the computer for the settings to take effect.
* Add the users to the PDF Generator User Accounts in Administration Console. Start by selecting **Home > Services > PDF Generator > User Accounts** and then **Add a PDFGUser providing valid credentials**. This change requires an application server restart.
* Run the Acrobat_for_PDFG_Configuration.bat command at directory C:\Adobe\Adobe LiveCycle ES4\pdfg_config (or where you installed LiveCycle ES4). This command copies some dynamic library files used by PDF Generator to the correct places.
* Run the SystemReadinessTool: Open a command window and change directory to <LC_Install_Dir>\pdfg_srt. Issue the command SystemReadinessTool .vbs <outputDir>, where <outputDir> is an arbitrary directory to store the generated reports. After the command has finished, review the SRT Report HTML file at the <outputDir> directory. Ensure that there are no error messages or warning messages related to the applications you plan to convert. For example, if you want to convert Microsoft Excel files, make sure that the row with Microsoft Excel has a green check sign. And also ensure that the row with PDFMaker DLL registered.
* For some applications, there is an initial setup phase the first time the user uses the program, such as OpenOffice. Review the screens to enable the user to use the program. Start by logging in to the operating system as PDFUser1, PDFUser2, or any users that you listed as PDF Generator users in Administration Console. Run the application, for example OpenOffice, and dismiss all activation dialog boxes.

##Running the sample

* Open the collateral folder within the downloaded ZIP file (Adobe-Samples-Service-PDFGenerator.zip). Copy a test file to the watched folder's input directory (by default it is C:\tmp\LCSamples\WatchedFolder\OptimizePDF\input on Windows).  
  Once the file is dropped into the input directory, Document Services/LiveCycle automatically picks it up and does the optimization.
* Check the optimized PDF file in C:\tmp\LCSamples\WatchedFolder\OptimizePDF\result on Windows

##Legal disclaimer

Any references to company names, company logos and user names in sample material or sample forms included in this documentation and/or software are for demonstration purposes only and are not intended to refer to any actual organization or persons.

Service Sample - Document Services/LiveCycle ES4 Service - PDF Generator-Convert All File Types To PDF - 07/15/2011 2:50 PM 
August 2011 
