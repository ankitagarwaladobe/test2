#Reader Extensions - Dynamically Apply Policy

Overview of the sample
----------------------

The sample demonstrates how to dynamically apply reader extensions to a PDF document. The process is initiated with a PDF document. An XML file containing the reader extensions credentials  
required to be applied being placed in a watched folder. The process applies the required reader extensions credentials and places the updated file back into the watched folder.

Ensure that you have Adobe Reader installed to be able to view the documents with the before and after processing.

Files needed for the sample
---------------------------

* **Adobe-Samples-Service-ReaderExtensions.lca** -- `The archive used for deploying the sample`.
* **collateral\Rights.xml** --	`Testing file containing the rights to be applied to the document`.
* **collateral\SampleToApplyRights.pdf** -- `The testing PDF document to be applied rights`.

Deploying the sample
--------------------

**Tip:** To deploy multiple samples, use the Samples Deploy Utility.

**Note:** These instructions assume that ADEP-Document Services/LiveCycle ES4 is installed on the C: drive on Microsoft Windows. If you have installed to a different location, substitute the directory where you installed Document Services/LiveCycle ES4.

* Check the following folder in the file system on the server where Document Services/LiveCycle is installed, if it exists, delete it before proceeding

**Windows** - `C:\tmp\LCSamples\WatchedFolder\ReaderExtensions`  
**Unix** - `/tmp/LCSamples/WatchedFolder/ReaderExtensions`  
* Log in to **Administration Console**.
* Click **Services > Applications and Services > Application Management**.
* Click the **LiveCycle Applications** tab and click **Import**.
* Click **Browse** to locate the sample archive (LCA) file Adobe-Samples-Service-ReaderExtensions.lca, and then click **Preview**.
* Select **Deploy** assets to runtime when import is complete and click **Import**.

Configuring the sample
---------------------

**Configure Credentials**

In the following steps, you need a credential file:

* generic Reader Extensions credential - available for download from http://www.adobe.com/go/reader_ext_cert. The zip file includes a .pfx file and a text file with the password. Save these files on your local machine.
* Log in to Administration Console (http://[hostname]:[port]/adminui).
* Click **Home > Settings > Trust Store Management > Local Credentials**.
* Click **Import** and on the Import Credential page specify this information:

```
   Trust Store Type: Reader Extensions Credential
   Alias: SampleReaderExtensionsCredential
   Credential: the pfx file located in the zip file downloaded from http://www.adobe.com/go/reader_ext_cert.
   Password: password is in the text file located in the zip file downloaded from http://www.adobe.com/go/reader_ext_cert.
```

* Click **OK** to import the credential. 
* Log in to Workbench.
* If **Samples - Reader Extensions** does not show in the Applications view, click **File > Get Application**.... Choose **Samples - Reader Extensions > Samples - Reader Extensions/1.0** from the application list to import the application to Workbench.
* Open the process **Dynamically Apply Rights**.
* Double-click the **Apply Usage Rights** activity to open its properties sheet. Click **Input > Credential Alias**, ensure that SAMPLEREADEREXTENSIONSCREDENTIAL is selected in the list. If not, check out the process first, and choose SAMPLEREADEREXTENSIONSCREDENTIAL in that list, then save the process and check in the process, finally deploy the application.

**Configure Watched Folder**

This step is optional if you do not want to change the default watched folder path.

The path of the WatchedFolder startpoint is C:\tmp\LCSamples\WatchedFolder\ReaderExtensions by default for Windows, and /tmp/LCSamples/WatchedFolder/ReaderExtensions for Unix. If you want to change this path, complete the following steps:

* Log in to Workbench.
* If **Samples - Reader Extensions** does not show in the **Applications** view, click **File > Get Application**.... Choose **Samples - Reader Extensions > Samples - Reader Extensions/1.0** from the application list to import the application to Workbench.
* In the Applications view, click **Samples - Reader Extensions> Samples - Reader Extensions/1.0> Processes >Dynamically Apply Rights**. To check out the process, right-click **Dynamically Apply Rights** and select **Check Out**.  
  To edit the process, right-click **Dynamically Apply Rights** and select **Open**.
* Click the startpoint **Dynamically Apply Rights - startpoint**, and in **Process Properties > General > Path**, you can enter (for example):  
**Windows** - `D:\temp\LCSamples\WatchedFolder\ReaderExtensions`  
**UNIX** - `/home/yourUserName/LCSamples/WatchedFolder/ReaderExtensions`

* To save the process, select *File > Save*.
* In the Applications view of Workbench, click **Samples - Reader Extensions> Samples - Reader Extensions/1.0**. To check in the application, right-click **Samples - Reader Extensions/1.0** and select **Check In**. 
  To deploy the process, right-click **Samples - Reader Extensions/1.0** and select **Deploy**.

Running the sample
------------------

* Navigate to the directory where Adobe-Samples-Service-ReaderExtensions.zip is extracted. Open the PDF, SampleToApplyRights.pdf, in collateral folder with Adobe Reader. Compare this document with the one with reader extensions later in step 4.
* Copy the folder collateral, which contains the two files SampleToApplyRights.pdf and Rights.xml, to the watched folder's input directory. By default C:\tmp\LCSamples\WatchedFolder\ReaderExtensions\input for Windows and /tmp/LCSamples/WatchedFolder/ReaderExtensions/input for Unix. The collateral folder is located in the folder where Adobe-Samples-Service-ReaderExtensions.zip is extracted.
* After a while, go to the watched folder's result directory, by default is C:\tmp\LCSamples\WatchedFolder\ReaderExtensions\result\yyyy\mm\dd\ for Windows and /tmp/LCSamples/WatchedFolder/ReaderExtensions/result/yyyy/mm/dd/ for Unix.
* Open the output PDF file SampleAppliedRights.pdf with Adobe Reader. Ensure that you use Adobe Reader but not Adobe Acrobat, for only Adobe Reader can show that the rights are applied.
* Compare the two documents. The SampleAppliedRights.pdf has the extended feature but the SampleToApplyRights.pdf does not. For example, the Rights.xml by default enables comments and digital signatures as below.

```
<rights>
        <formFillIn enabled="0"/>
        <formDataImportExport enabled="0"/>
        <comments enabled="1"/>
        <commentsOnline enabled="0"/>
        <submitStandalone enabled="0"/>
        <onlineForms enabled="0"/>
        <barcodeDecoding enabled="0"/>
        <digitalSignatures enabled="1"/>
        <embeddedFiles enabled="0"/>
        <dynamicFormFields enabled="0"/>
        <dynamicFormPages enabled="0"/>
</rights>
```

Notice that the SampleAppliedRights.pdf has comments and digital signatures toolbar where the SampleToApplyRights.pdf does not, indicating that the output file was applied reader extensions successfully.

And if you are using Adobe Reader X, the location of the toolbar for Sign and Comment is different with the figure above showed.

**Next steps**

Try changing the rights to be applied (0 means disable and 1 means enable). Run this process again and check if the corresponding features are enabled.

**Legal disclaimer**

Any references to company names, company logos and user names in sample material or sample forms included in this documentation and/or software are for demonstration purposes only and are not intended to refer to any actual organization or persons.

Service Sample - Document Services/LiveCycle ES4 - Reader Extensions - Dynamicaly Apply Policy - 08/03/2011 8:15 PM 
August 2011
