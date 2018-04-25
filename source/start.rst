###############
Getting started
###############

This part of the documentation provides a first steps guide for quickly setting up an application with ViUR. The following chapters will go much deeper into ViUR, its architecture and how it is used. The Google App Engine™ is only introduced shortly here. Knowledge on what it is, how it works and how an application is registered there is required, before continuing.

=============
Prerequisites
=============

ViUR runs on top of the Google App Engine™ (GAE). This means, that a ViUR application needs to be deployed to the Google Cloud Platform when it is run on the internet. For the deployment as well as a local development and testing environment, Google offers the **Google App Engine SDK for Python** for free on `<https://cloud.google.com/appengine/downloads#Google_App_Engine_SDK_for_Python>`_.

There are two ways to get the SDK run on your machine:

1. Manually download and install the SDK natively from the above location for your particular operating system. Windows, Mac OS and Linux are supported. In case that Linux is used, the particular package manager should be consulted first, maybe it already supports packages for the Google App Engine SDK for Python.

  It is also required to have a working **Python 2.7** installation on your machine. This can be obtained from `python.org <https://www.python.org>`_, but may be pre-installed already when you are on Linux or Mac OS.

2. If you are familiar with Docker, we also offer several *ViUR docker recipes* to quickly set up a dedicated, Linux-based build-environment, with all prerequisites installed. To make use of these, just visit `<https://hub.docker.com/u/viur/>`_.

======================================
Setting up a ViUR project from scratch
======================================

Setting up a new ViUR project is easy, and takes only a few steps for getting a working result. Make sure that the :ref:`Prerequisites` described above are installed so far, and Python is in your PATH.

The way described here only provides a basic stub for a fresh ViUR project to start from. It has no functionality at all. If you want to start with a pre-configured example project, take a look at :ref:`Setting up the demo project`.

1. Create an empty project folder of your choice in a location of your choice. Change into this location.

2. Download the latest setup.py script from `<https://www.viur.is/download>`_. It can be directly obtained by the link `<https://www.viur.is/package/download/setup/latest>`_.

3. Run ``python setup.py``. On Windows, just double-clicking the file ``setup.py`` should do the job.

4. The setup utility determines the project name from the project directory. This should be the same name as the unique application identifier registered for the application on GAE, if deploying is wanted. Enter a project-name or confirm the default one.

5. Confirm the installation when the correct folder is prompted. The setup utility then will write all necessary files and download the current server and vi.

Then, you're done! The app can now be locally run with ``dev_appserver.py -A <your-app-id> .`` from the terminal (Linux, Mac OS) or from the *Google App Engine Launcher* (Windows, Mac OS). By default, the app runs on port 8080 (`<http://localhost:8080>`_), or with the port provided by the *Google App Engine Launcher*.

Below is an example for a few commands on a Linux terminal to setup a clean ViUR project from scratch:

.. code-block:: bash

   mkdir hello-viur                                                      # Setup project folder
   cd hello-viur                                                         # Change into this folder
   wget -qO setup.py https://www.viur.is/package/download/setup/latest   # Download latest setup
   python setup.py                                                       # Run ViUR setup tool
   dev_appserver.py -A hello-viur .                                      # Start Google App Engine


When you see a friendly "Hello World" welcoming you in your browser, your app is running!
The Vi can be access at `<http://localhost:8080/vi>`_, or under your particular port.

.. figure:: images/start-vi.png
   :scale: 60%
   :alt: The Vi after setting up a scratch project.

   The Vi after setting up a scratch project.


.. Note::

   For a professional project setup, we recommend to use our pre-configured repository, which can be found at `<https://github.com/viur-framework/base>`_.

   Simply clone it and afterwards run ``clean-base.py`` to obtain a stand-alone repository which can immediately be executed and pushed elsewhere. See the README-file of the repo for further help!

---------------------------
Logging into the new system
---------------------------

On the first startup, ViUR creates an new admin-user named ``admin@<your-app-id>.appspot.com`` with a random password within the database. This password is printed to the server debug console, where you have to copy it out.

Watch out for a line like this:
::
   ViUR created a new admin-user for you! Username: admin@myapp.appspot.com, Password: SU7juUIb1F2aZ

When the system is started in the cloud for the first time, an e-mail with this password is sent to all application administrators.

Alternatively, you can login with a simulated Google user. Both login forms are provided by the default server and can be done using the Vi.

