.. VistA documentation master file, created by
   sphinx-quickstart on Mon Dec 17 16:27:57 2012.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to the VistA documentation!
=========================================================
.. figure:: http://code.osehra.org/content/named/SHA1/c0286b38-OSEHRA_LogoText.png

Instructions for Establishing and Testing the OSEHRA Code Base
---------------------------------------------------------------

These pages describe the steps required to obtain the OSEHRA open source VistA codebase from the OSEHRA code repository, establish a working test environment, execute the tests, and view the results on the OSEHRA Software Quality Dashboard.

The instructions comprise of the following sections:

.. toctree::
  :maxdepth: 2
  
  ObtainingandInstallAuxPrograms
  ChoosingMUMPSEnvironment

For the following two sections, follow the instructions based upon which type of MUMPS database will be utilized:

Cache:

.. toctree::
  :maxdepth: 1
  
  InstallCache
  ImportCache
  
GT.M:

.. toctree::
  :maxdepth: 1  
  
  InstallGTM
  ImportGTM
  
The last sections are common to both types of systems:

.. toctree::
  :maxdepth: 2

  ObtainingTestingCode  
  SetupTestingEnvironment
  RunningandUploadingTests
  ReviewingResults

Troubleshooting:
````````````````

To report a problem or see potential solutions visit the `Troubleshooting Page`_


Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`


.. _`Troubleshooting Page`: http://www.osehra.org/wiki/troubleshooting-installation-and-testing