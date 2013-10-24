#PDF Generator - Convert All File Types To PDF

Overview of the sample
----------------------

This sample demonstrates how you can easily convert different formats of files to PDF by using the PDF Generator service.

The PDF Generator service converts the following types of files into PDF. Note it is necessary to install the specific application on the system for the types of files you want to convert. For example, if you want to convert Microsoft Visio files, install Microsoft Visio on the system where Document Services/LiveCycle ES4 is installed.

Type|	Version	        |Extension	|Note	|Platform
----| --------------- |----       |---  |--------
Microsoft Office |	2003 |DOC, XLS, PPT, WPD, RTF, TXT| A filename extension is not required for the conversion to work.|	Windows
Microsoft Office |	2007 |DOCX, XLSX, PPTX|	|	Windows
Microsoft Visio |	2003, 2007 |VSD| |Windows
Microsoft Project| 2003, 2007|MPP| |Windows
AutoCAD|	2005 - 2009|DWG, DXF, DWF|Can only run on Windows 2003 32 bit|	Windows
WordPerfect|12, X4|WPD||Windows
FrameMaker|7.2, 8|FM||Windows
PageMaker|7.0|PMD, PM6, P65, PM||Windows
OpenOffice|2.4.2, 3.1.0|ODT, ODS, ODP, ODG, ODF, SXW, SXI, SXC, SXD, SXM, DOC, XLS, PPT, TXT, RTF, WPD, DOCX, SLSX, PPTX||Windows/Linux/Solaris
Print files||PS, PRN, EPS||All (Including AIX)
Web pages||HTML, HTM, ZIP (archive of HTML files)|ZIP file containing HTML files can be converted as well. The archive must follow one of the following two rules: 1) On the archive root, there can be only one HTML file. 2) On the archive root, if there is more than one HTML file, one of them must be named  index.html or index.htm.|All (Including AIX)
Image files||JPEG, GIF, BMP, TIFF, PNG, JPG, TIF, JPF, JPX, JP2, J2C, JPC||All (Including AIX)
videos||SWF, FLV||Windows

**Note**: Some applications are supported only specific OS:

* Windows Only: Microsoft Office, Microsoft Visio, Microsoft Visio, WordPerfect, FrameMaker, PageMaker, Flash
* Windows/Linux/Solaris: OpenOffice
* All (Including AIX): Print files, web pages, Image Files

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

**Configure Windows 2008 x64 Enterprise Server to run PDF Generator**

To run this sample successfully, ensure that PDF Generator is enabled. The following steps are required to enable PDF Generator on a Windows 2008 x64 Enterprise Server. If PDF Generator is configured during Document Services/LiveCycle installation, skip this step. Check with your system administrator to find out whether PDF Generator is configured.

* Create at least two users with Administrative privileges in the Windows operating system, for example, "PDFGUser1" and "PDFGUser2".
* Disable **UAC** for these users: to turn UAC off, go to **Control Panel > User Accounts > Turn User Account Control on or off**. Deselect **Use User Account Control (UAC) to help protect your computer** and click **OK**. Restart the computer for the settings to take effect.
* Add the users to the PDF Generator User Accounts in Administration Console. Start by selecting **Home > Services > PDF Generator > User Accounts** and then **Add a PDFGUser providing valid credentials**. This change requires an application server restart.
* Run the Acrobat_for_PDFG_Configuration.bat command at directory C:\Adobe\Adobe LiveCycle ES4\pdfg_config (or where you installed LiveCycle ES4). This command copies some dynamic library files used by PDF Generator to the correct places.
* Run the SystemReadinessTool: Open a command window and change directory to <LC_Install_Dir>\pdfg_srt. Issue the command SystemReadinessTool .vbs <outputDir>, where <outputDir> is an arbitrary directory to store the generated reports. After the command has finished, review the SRT Report HTML file at the <outputDir> directory. Ensure that there are no error messages or warning messages related to the applications you plan to convert. For example, if you want to convert Microsoft Excel files, make sure that the row with Microsoft Excel has a green check sign. And also ensure that the row with PDFMaker DLL registered.
* For some applications, there is an initial setup phase the first time the user uses the program, such as OpenOffice. Review the screens to enable the user to use the program. Start by logging in to the operating system as PDFUser1, PDFUser2, or any users that you listed as PDF Generator users in Administration Console. Run the application, for example OpenOffice, and dismiss all activation dialog boxes.

**Additional setup for specific file types**

* For some applications, there is an initial setup phase the first time the user uses the program, such as OpenOffice. Review the screens to enable the user to use the program. Start by logging in to the operating system as PDFUser1, PDFUser2, or any users that you listed as PDF Generator users in Administration Console. Run the application, for example OpenOffice, and dismiss all activation dialog boxes.
* If you want to convert the following types of files to PDF, add the corresponding Path variable to the system environment. 

Type                          |  Path variable |	Example
----                          |  ------------- | --------
Corel WordPerfect 12, X4 (WPD)|	WordPerfect_PATH |WordPerfect_PATH = c:\Program files\Corel\Suite8\wdp.exe
Adobe FrameMaker ® 7.2, 8 (FM)|	FrameMaker_PATH	 |FrameMaker_PATH=c:\Program files\FrameMaker\framemaker.exe
Adobe PageMaker ® 7.0 (PMD, PM6, P65, PM)|PageMaker_PATH|PageMaker_PATH=c:\Program files\PageMaker\pagemaker.exe
OpenOffice 2.4.2, 3.1.0 (ODT, ODS, ODP, ODG, ODF, SXW, SXI, SXC, SXD, SXM)|OpenOffice_PATH|OpenOffice_PATH = C:\Program Files\OpenOffice.org 3.1\ (Note the OpenOffice_PATH is different from the others. This variable is set to the OpenOffice installation folder (instead of the path to the executable). )
Adobe Photoshop CS2|Photoshop_PATH|Photoshop_PATH = C:\Program Files\Adobe\Adobe Photoshop CS2\Photoshop.exe

##Running the sample

* Open the collateral folder within the downloaded ZIP file (Adobe-Samples-Service-PDFGenerator.zip). Copy a test file to the watched folder's input directory (by default it is Path is: C:\tmp\LCSamples\WatchedFolder\ConvertAllFileTypesToPDF on Windows and /tmp/LCSamples/WatchedFolder/ConvertAllFileTypesToPDF on Unix). Once the file is dropped into the input directory, Document Services/LiveCycle automatically picks it up and does the conversion.
* Check the converted PDF file in C:\tmp\\LCSamples\WatchedFolder\ConvertAllFileTypesToPDF\result on Windows or /tmp/LCSamples/WatchedFolder/ConvertAllFileTypesToPDF/result on Unix.

##Legal disclaimer

Any references to company names, company logos and user names in sample material or sample forms included in this documentation and/or software are for demonstration purposes only and are not intended to refer to any actual organization or persons.

Service Sample - Document Services/LiveCycle ES4 Service - PDF Generator-Convert All File Types To PDF - 07/15/2011 2:50 PM 
August 2011 
