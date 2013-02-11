Set up the Testing Environment
===============================

.. toctree::


.. role:: usertype
    :class: usertype

To configure the environment for testing, start the cmake-gui.exe. Once it has started (Figure 73), set the two paths at the top of the window so that the source code points to the Testing Source Directory from step 1 above. This directory will point to a directory (folder) containing CMakeLists.txt file. The Binaries path can go to a folder of your choice, but note that whatever directory is provided will be the Testing Binary Directory, and after configuration, it will contain CMake files defining the tests to be run.

Once those are set, click the Configure button. The interface will then ask you to specify a generator (Figure 74). These are normally used to check for working C and C++ compilers. For VistA testing, the generator does nothing and it therefore not used. This selection can be chosen arbitrarily to any displayed generator so we recommend selecting the default value. Click finish after the selection is made to continue the configuration process.


.. figure:: http://code.osehra.org/content/named/SHA1/e7e145f2-CMakeGUIHighlights.png
   :align: center

   Figure 73 - Initial cmake-gui page.


.. figure:: http://code.osehra.org/content/named/SHA1/6f19f446-CMakeGUIGeneratorSelection.png
   :align: center

   Figure 74 - Generator selection.

Following generator selection, the interface will produce a highlighted display such as in Figure 75 for Linux and Figure 76 for Windows. The entries in the window are the variables which can be set to control the testing process. Most of the values should be set correctly by the automated configuration process, but the scripting environment and the location of the VistA source code may need to be set appropriately. To aid in the configuring, most variables have a mouse-over tip which explains in greater detail what the variable should contain.


.. figure:: http://code.osehra.org/content/named/SHA1/26d73c05-CMakeGUILinuxPostConfig.png
   :align: center

   Figure 75 - Linux interface after generator selection is complete.


.. figure:: http://code.osehra.org/content/named/SHA1/c58f3fa3-CMakeGUIWinPostConfig.png
   :align: center

   Figure 76 - Windows interface after generator selection is complete.

NOTE: The "Found" messages for each of the programs will only be displayed on the initial configuration of the system.  To see the variables at a later date, follow the instructions at the bottom of this page.

Looking first at the Windows example with Cache (Figure 77), three variables corresponding to  CTerm, CControl, and VISTA_Path need to be set or verified according to the values in Figure 78.



.. figure:: http://code.osehra.org/content/named/SHA1/561b18ff-CMakeGUISetVariable.png
   :align: center

   Figure 77 - Setting the VistA variables for Cache and Windows. The pop-up shows setting the VISTA_Path.  The tool-top for this entry reads \"Path to the VistA folder within Cache\".

Once the variables needed for the MUMPS environment are set, press \"Configure\" again to accept the changes into the environment and then press \"Generate\" to complete the process.

The following table has a list of some of the import variables to be set prior to testing and the description of the variable.


     =====================   ===================================  ==================================
      Variable Name           Value for Testing in Cache          Value for Testing in GT.M
     =====================   ===================================  ==================================
        CControl              Path to CControl Executable                        N/A
        CTerm                 Path to CTerm Executable                           N/A
        GTMPROFILE                        N/A                         Path to gtmprofile file
        VISTA_GLOBALS_DIR                 N/A                         Path to folder with database.dat
        VISTA_ROUTINES_DIR                N/A                         Path to folder with VistA Routines
        OSEHRA_PATH           Path to folder of OSEHRA Code base   Path to folder of OSEHRA Code base
        INSTANCE              Name of Cache Server                               N/A
        NAMESPACE             Namespace created when installing                  N/A
                              Cache
     =====================   ===================================  ==================================

After setting the variables and configuring a second time, the red color of the variables that have been set will disappear and any new variables will be highlighted

.. figure:: http://code.osehra.org/content/named/SHA1/e280c1dd-CMakeGUIWinSecondConfig.png
   :align: center

   Figure 79 - Setting the VistA variables for Intersystems Cache on Windows.

For the Linux example with GT.M (Figure 75), four variables corresponding to EXPECT_EXEC, GTMPROFILE, and VISTA_GLOBALS_DIR, and VISTA_ROUTINES_DIR need to be set or verified according to the values in Figure 78.

There is an option that is not needed to run the testing but may become useful. The CLEAN_DATABASE option will show up during configuration of the VistA Testing.  It uses a series of Python scripts to clean the database of the VistA instance.   This would all be done during the build phase of a nightly dashboard submission. If you choose not to use this option and have followed the above steps, you can continue to running the tests.

To utilize this option on Cache, the CLEAN_DATABASE checkbox must be checked to tell CMake to configure the correct files. You will also need to create a new cache.dat using the steps from earlier (starting at Figure 15) and set the PRISTINE_CACHE_DAT_PATH to point to the location of that newly created cache.dat.  It will then shut down the Cache instance, copy the empty database in place of the old one, restart Cache, then collect and import the OSEHRA routines and globals.  The Cache CLEAN_DATABASE

On GT.M, the CMake side is more simple.  Only the CLEAN_DATABASE option needs to be set during configuration. The scripts will , at build time, proceede to delete the database.dat and the 'r' folder where the routines are stored.  Then, create a new database.dat and 'r' folder and import the routines and globals from the OSEHRA Code Base.

If you plan to use these options, there are more variables that need to be set:

     ========================   ===================================  ==================================
         Variable Name           Value for Testing in Cache          Value for Testing in GT.M
     ========================   ===================================  ==================================
      CLEAN_DATABASE                     	ON                                     	ON
      PRISTENE_CACHE_DAT_PATH   Path to folder containing an empty                 N/A
                                cache.dat
      PYTHON_EXECUTABLE         Path to Python Executable             	Path to Python Executable
      GIT_EXECUTABLE            Path to Git Executable	                Path to Git Executable

     ========================   ===================================  ==================================

How to find Git and Python information:
To see the value that is set for GIT_EXECUTABLE or PYTHON_EXECUTABLE after configuration, click on the \"Advanced\" toggle in the CMake GUI (Figure 79A).  This option is used to display other variables that have been configured, but should not require modification to run the testing.  This is where the new search program will place GIT_EXECUTABLE and PYTHON_EXECUTABLE and the proper values.  Example values are shown in Figures 79B and 79C.


.. figure:: http://code.osehra.org/content/named/SHA1/7737fdf1-CMakeAdvancedBox.png
    :align: center

    Figure 79A - CMake GUI with the Advance toggle labeled

.. figure:: http://code.osehra.org/content/named/SHA1/2a67ceca-CMakeGitExecHighlighted.png
    :align: center

    Figure 79B - Advanced variables with GIT_EXECUTABLE highlighted

.. figure:: http://code.osehra.org/content/named/SHA1/41389cc0-CMakePythonExecHighlighted.png
    :align: center

    Figure 79C - Advanced Variables with PYTHON_EXECUTABLE highlighted



Functional Testing of the CPRS GUI
----------------------------------

The most recent commit to the VistA repository introduced the ability to use an open-source tool called Sikuli to test the CPRS and Vitals Manager interface.  Sikuli is a cross-platform GUI testing system which uses OpenCV and Jython, a combination of Java and Python, to match a script of supplied screenshots and act upon them.  Due to the limitations of CPRS, this tool will only be utilzed on Windows environments, but it will work on any platform.  The Functional Testing consists of two parts: The PostImportSetupScript and the Sikuli folder.  The PostImportSetupScript is a python file, designed to be run right after import from the OSEHRA repository,which connects to the VistA system and sets up an institution for testing.  This includes setting up a demonstration domain, setting the correct box:volume pairs, and adding other laboratory tests and data.  The script will also add a sample patient, doctor and nurse, with their necessary security keys.  After the PostImportSetupScript is run, the Sikuli test starts and will look to click on icons on the user's desktop to start both programs.  The scripts also cause VistA to expect to interact with certain versions of each of the software.  Those versions are available for download from here.  The instructions for setting up the short cuts are on the download site.

When running the CMake GUI, the option to use the CPRS Functional Testing is called SIK_SYSTEM_TESTING

.. figure:: http://code.osehra.org/content/named/SHA1/e4d2837b-CMakeSikTestingHighlighted.png
    :align: center

    Figure 80A: Showing the new option in the CMake GUI.

After Pressing configure you can see some new variables come up.  There is a difference when running this VISTA_CPRS_FUNCTIONAL_TESTING on the various supported platforms.  On all platforms, the CPRSPostImport test is created, which asks for a VISTA_SITE_NAME.  This variable defaults to DEMO.OSEHRA.ORG.  On the GT.M systems, this test is accompanied by a warning, voiced during configuration, that tells the user to make a particular code change before running the Functional Testing.  The PostImportSetupScript uses DINIT, which has a known failure of attempting to release a lock that was created before the transaction. (https://groups.google.com/forum/#!topic/hardhats/-cJxbX_Re1c).

.. figure:: http://code.osehra.org/content/named/SHA1/accd2626-CMakeVistASiteHightlighted.png
    :align: center

    Figure 80B: Showing the VISTA_SITE_NAME variable and the warning on a GT.M on Linux instance.

On Windows, the warning will not be shown and a second variable will be created which asks for the path to the Sikuli batch file.

.. figure:: http://code.osehra.org/content/named/SHA1/7e675021-CMakeSikuliVistASiteHighlighted.png
    :align: center

    Figure 80C: Showing the SIKULI_EXECUTABLE and VISTA_SITE_NAME variable on a Cache on Windows instance.

After a round of configuring and generating, the new tests will be created and can be executed like the others.


Functional Testing of VistA via the Roll and Scroll Menus
``````````````````````````````````````````````````````````

The VistA repository also has the capability to test the local VistA instance through the Roll and Scroll (RAS) menu interface.

.. figure:: http://code.osehra.org/content/named/SHA1/ecc66b5c-CMakeRasTestingHightlighted.png
    :align: center

    Figure 81A: Showing the RAS_SYSTEM_TESTING option in the CMake GUI.

There are currently two test suites that utilize the RAS functionality:  Scheduling and Problem List.  Before these tests can be run, there is one more variable to be set named RAS_SYSTEM_TESTING:

.. figure:: http://code.osehra.org/content/named/SHA1/7e8b6926-CMakeTestResultsHightlighted.png
   :align: center

The TEST_RESULTS_DIR is used to set the file location where the log and result files from the tests will be stored.  After configuration, these tests will be added to the queue.