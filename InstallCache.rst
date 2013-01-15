Installing Cache
=============================

.. toctree::


.. role:: usertype
    :class: usertype
    
The following instructions were adapted from Nancy Anthracite\'s document entitled InstallingVistAWithSingleUserVersionCache5.2, which was created to guide a user through installing InterSystems Cache onto a Windows operating system. The instructions were using an older version of Cache; this uses the most recent trial version and shows the most recent Management Portal interface.

Trial versions of the Cache installer can be downloaded from http://download.intersystems.com/download/register.csp. This installation guide uses Cache 2011.1. If you already have a Cache installation and are looking to install VistA as an additional database, you do not have to re-install Cache. Please use your existing installation and pick up the instructions at the point where the folder is created within the mgr folder.

Download and Install Cache
--------------------------

Download the Cache installer from the above link and double click on the downloaded  .exe file. The first window that requires interaction is the Licensing Agreement shown in Figure 1. Agree to the license in order to continue in the installation process.

.. figure:: http://code.osehra.org/content/SHA-1/df177515fc3ae09c5e9cd6db81990a81dde38091-Cache2011License.png
   :align: center

   Figure 1 - Cache License Terms

The next window, Figure 2, asks to set the directory in which Cache will be installed. Most users will be able to accept the default path. If more than one instance is found on the machine, the next instances will be denoted with a number appended to the end of the instance name.


.. figure:: http://code.osehra.org/content/SHA-1/3c138d88283028d6df4394471d7deb459c7bd2ae-Cache2011InstallPath.png
   :align: center

   Figure 2 - Setting the installation path for Cache

Once the install directory is set, the installer will display a summary of the instance that will be installed in the process, Figure 3. There is the option to enter a license if you have one, but this is not a required step for the current testing configuration. Figure 4shows the final screen of the installation process.


.. figure:: http://code.osehra.org/content/SHA-1/85434e9e11340bccee0fa4fe0a7deff629d995e4-Cache2011InstallSummary.png
   :align: center

   Figure 3 - Summary of Cache installation options


.. figure:: http://code.osehra.org/content/SHA-1/46c175c70803fa9dae10bb8944959fb590995675-Cache2011InstallComplete.png
   :align: center

   Figure 4 - Final window of Cache Installation

The first sign of a correctly installed and running instance of Cache is the Cache Cube in the taskbar shown in Figure 5.


.. figure:: http://code.osehra.org/content/SHA-1/d3df0e664729374dda029474f9e6024962de537b-Cache2011Cube.png
   :align: center

   Figure 5 - Screenshot of Cache Cube in taskbar.

.. figure:: http://code.osehra.org/content/SHA-1/31e127889ad9b72a09c6d7295777e1a32a1996a2-Cache2011MenuDoc.png
   :align: center


   Figure 6 - The main menu that shows when the Cache Cube is clicked.

Clicking on the Cube will open a menu, Figure 6, that displays the options to interact with the Cache database. The next test to ensure that your Cache instance is working is to open the documentation. This will bring up the documentation home page in your default web browser (Figure 7).




.. figure:: http://code.osehra.org/content/SHA-1/83e31c7b90c6d3707feb8cec6fe797a6e33fda3f-Cache2011DocMainPage.png
   :align: center

   Figure 7 - Documentation font page in the web browser Google Chrome.



.. figure:: http://code.osehra.org/content/SHA-1/716a8551c4804cd9012a0a62c6465de7fbfb13b6-Cache2011DocSearch.png
   :align: center


   Figure 8 - The search window of the Cache documentation.

Configuring Cache
------------------

Once Cache is installed, it is time to create the proper folders and environment to run the VistA instance within Cache. The first step is to go to the mgr folder of Cache and create a new folder as in Figure 9. This folder will hold the database file cache.dat that will contain the VistA routines and globals.


.. figure:: http://code.osehra.org/content/SHA-1/0f2c2ab60a0fed287cd15c14c23ecc37a4999297-Cache2011MgrFldr.png
   :align: center


   Figure 9 - mgr folder prior to creation of VistA folder

In the example shown in Figure 10, the folder has been given the name \"VistA.\" While the choice of name has no bearing on the installation, the testing code requires that the Namespace name chosen in Figure 21matches the folder name created in this step.

.. figure:: http://code.osehra.org/content/SHA-1/18a90c5b4c1586a7df2f0f1413f0e0e815f65981-Cache2011MgrFldrVistA.png
   :align: center

   Figure 10 - mgr folder post-creation of VistA folder

At this point we are ready to stand up the VistA instance. Right click on the Cache cube and select Management Portal of Cache (Figure 11). This link will open a Management Portal web page as shown in Figure 12.  Click on System Administration to show administrative options.

.. figure:: http://code.osehra.org/content/SHA-1/1f2af02fb6c2301186db8660746f68515adeb49c-Cache2011MenuSysMgt.png
   :align: center

   Figure 11 - Management Portal link in Cache

.. figure:: http://code.osehra.org/content/SHA-1/747ca57e3f7f358999dd1c3b2d829b64802a13be-Cache2011SysMgtMain.png
   :align: center

   Figure 12 - Main page of the Management Portal

System Administration shows those options that can be used to change the Cache system. Our goal is to use the Configuration function to create and initialize an empty database that can then be filled with the VistA routines and globals. Starting from Figure 13, click on Configuration, System Configuration, and Local Databases to arrive at Figure 14.

.. figure:: http://code.osehra.org/content/SHA-1/f36ea51c95efaab7bf6a2ffe873401a5fbf309f5-Cache2011SysAdminMenu.png
   :align: center

   Figure 13 - System Administration page of Management Portal

Create the database by clicking on the Local Databases tab and then selecting Go.


.. figure:: http://code.osehra.org/content/SHA-1/f245cb17376cbd543279d0a3226b1ba276b6b735-Cache2011SysConfigMenu.png
   :align: center


   Figure 14 - System Configuration menu.

This resulting page contains the list of all of the local databases Figure 15. All of the selections shown were created automatically during the installation of Cache. Create a new database by clicking on the \"Create New Database\" button. This will bring up a wizard (Figure 16).

.. figure:: http://code.osehra.org/content/SHA-1/2cc2f9eaafdd51acb865467181c86c88c465d847-Cache2011CreateDatabase.png
   :align: center

   Figure 15 - Local Databases page with pointer to Create New Database button.

Set the directory entry to the folder that you created (Figure 10) and set the database name. We recommend using the same name as the folder, but this is not necessary. When satisfied, select next to proceed to Figure 17.

.. figure:: http://code.osehra.org/content/SHA-1/eacb4e1c249f560e3dfd8a03df24d883a34e80ea-Cache2011DatabaseWizardName.png
   :align: center

   Figure 16 - First page of the Database Wizard.

It is not necessary to change any of the default settings to enable testing and we recommend simply hitting Finish to proceed to Figure 18. However, if there are known required settings for the current site, these settings can be modified. Verify that the newly created database appears in the database listing.

.. figure:: http://code.osehra.org/content/SHA-1/a0ead7464298cd7c0242dade9ceeda3638803493-Cache2011DatabaseWizardDetails.png
   :align: center

   Figure 17 - Details of the Database Wizard


.. figure:: http://code.osehra.org/content/SHA-1/73ac678dee47b28754fe9d1e04b25ce440dbba32-Cache2011ShowNewDatabase.png
   :align: center


   Figure 18 - Database listing with the inclusion of the recently created VistA database.

We now will configure the namespace for the newly created database. Navigate back to the System Configuration menu (Figure 19), click on the Namespaces option, and then click on the \"Create New Namespace\" button (Figure 20) to open a wizard (Figure 21).

.. figure:: http://code.osehra.org/content/SHA-1/24613b57a1a017712e90661fcd5a7580899579ea-Cache2011ConfigureNameSpace.png
   :align: center

   Figure 19 - Choosing Namespaces from System Configuration Menu

.. figure:: http://code.osehra.org/content/SHA-1/374ab64961abb09a79dc93573e1c0ada8453aa4e-Cache2011CreateNewNamespace.png
   :align: center

   Figure 20 - Namespace listing and button to create a new namespace.

In the wizard, enter the name of the namespace and then select the database created in Figure 16. Be certain to name the Namespace the same as the folder created in Figure 10. Click on \"Save\" to finish the Namespace creation and to return to the namespace listing.


.. figure:: http://code.osehra.org/content/SHA-1/6ea5a988fdc05d0ce93a51e9c3175a1524b5bde8-Cache2011NamespaceForm.png
   :align: center

   Figure 21 - Choosing the name of the namespace and the database it maps to.

Verify that the new namespace is now in the list of current namespaces (Figure 22).

The next steps will be configuring the global and routine mappings, both of which are accessed from this page. We will focus on the global mapping first.

 .. figure:: http://code.osehra.org/content/SHA-1/d5960250534d460ff2e05302f74ee4bbbfad7c99-Cache2011GlobalMappingSelect.png
    :align: center

    Figure 22 - Namespace listing with the new namespace in it. The boxes highlight the links for mapping globals and routines.

To create the new mapping, click on New Global Mapping (Figure 23).  This opens the wizard in Figure 24.

.. figure:: http://code.osehra.org/content/SHA-1/9fd555858b162986fcea472e1b166501786b9471-Cache2011NewGlobalMapping.png
   :align: center

   Figure 23 - Setting the Global Mapping.

For VistA, there is only one global mapping that needs to be made. First set the Global Database location to the VistA database name, and for the Global Name enter \"%Z*\". This will map all globals that start with \"%Z\" to be specific to the VistA namespace. Click OK and the wizard will exit and display the new mapping in the window (Figure 25). Be sure to click on Save Changes before navigating back to the Namespaces page.


.. figure:: http://code.osehra.org/content/SHA-1/3330d488766bb5848e07aca70320aecee6ae85b2-Cache2011SetGlobalMapping.png
   :align: center

   Figure 24 - Adding the %Z* mapping to the globals.


.. figure:: http://code.osehra.org/content/SHA-1/4c432905c78972874ffc6ba0d06952e39baac46d-Cache2011SaveGlobalMapping.png
   :align: center

   Figure 25 - Page displaying the newly mapped globals.

The final step before Cache is ready for the import is to map the routines. From within the Namespaces menu in the Management Portal, click on the Routine Mappings link (Figure 26) which will bring you to the page that lists the current routine mappings for the VistA namespace.


.. figure:: http://code.osehra.org/content/SHA-1/d12fc19d6f07e2781922232063841c26e16f570f-Cache2011RoutineMappingSelect.png
   :align: center

   Figure 26 - Selecting the namespace mapping link.

Much like the globals, there are no current mappings. Click on the New Routine Mapping button (Figure 27) to bring up the mapping wizard again (Figure 28).

.. figure:: http://code.osehra.org/content/SHA-1/7df74caea92b68fe6454443ef9e9cf0c2319539f-Cache2011NewRoutineMapping.png
   :align: center

   Figure 27 - Adding new Routine Mappings.

Again select the database location that corresponds to the VistA database, enter \"%DT*\" into the Routine name, and click Apply. This adds the first namespace mapping to the VistA database.


.. figure:: http://code.osehra.org/content/SHA-1/614140b7a09154ebb55af96ab0901aff684a8bb4-Cache2011SetRoutineMapping.png
   :align: center

   Figure 28 - Entering the first routine mapping.

There are six other mappings that need to be entered in the same manner -

+-------+
| %RCR  |
|       |
| %XU*  |
|       |
| %ZIS* |
|       |
| %ZO*  |
|       |
| %ZT*  |
|       |
| %ZV*  |
+-------+


After the final mapping is set, click OK to be sent back to the Routine Mapping page. You should now see the seven mappings from Figure 29listed on the page. Click on the Save Changes button.



.. figure:: http://code.osehra.org/content/SHA-1/76ede01b9e8086ae083fef2a87a1c44ccde7f2ff-Cache2011SaveRoutineMapping.png
   :align: center

   Figure 29 - Final listing of Routine Mappings and the Save Changes button.



The final step of preparing the Cache installation for testing is to set the instance to allow TELNET service. This is done though the System Administration > Security > Services menu (Figure 30).

.. figure:: http://code.osehra.org/content/SHA-1/	494cd956b66ff0212e7e74db1d428f71a20d86b2-Cache2011ServicesMenu.png
   :align: center

   Figure 30 - Menu path to the Services option.

Click on Go to be brought to the menu which lists all services that are supported by Cache. Near the bottom of the list you will see the \"%Service_Telnet\" listing (Figure 31). Click on the link to bring up the \"Edit Service\" page (Figure 32).


.. figure:: http://code.osehra.org/content/SHA-1/8af9b9f448e6ec9d483738d14364a9a5440bab35-Cache2011TelenetServiceoff.png
   :align: center

   Figure 31 - The list of Services available to Cache

.. figure:: http://code.osehra.org/content/SHA-1/	6f00d8172189a03fd3699175fabc7a6e90bf0851-Cache2011TelnetServiceEdit.png
   :align: center

   Figure 32 - Edit Service page for %Service_Telnet.

To enable the Telnet session, simply check the box next to \"Service Enabled\" and then click \"Save\" (Figure 33).


.. figure:: http://code.osehra.org/content/SHA-1/b2fe0970e2307bcb73852ce086412340cdc0de13-Cache2011EnableTelnetService.png
   :align: center

   Figure 33 - Enabling the Telenet service.

After saving, the Services menu will now show that the Telnet service is enabled (Figure 34).

.. figure:: http://code.osehra.org/content/SHA-1/a354a916f57c3a0ab164b2ea8228078a805a146b-Cache2011TelnetServiceEnabled.png
   :align: center

   Figure 34 - Services menu with Telnet enabled