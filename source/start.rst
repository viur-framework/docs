###############
Getting started
###############

This part of the documentation provides a first steps guide for quickly setting up an application with ViUR. The following chapters will go much deeper into ViUR, its architecture and how it is used. The Google App Engine™ is only introduced shortly here. Knowledge on what it is, how it works and how an application is registered there is required, before continuing.

=============
Prerequisites
=============

ViUR runs on top of the Google App Engine (GAE) platform for the Python Standard Environment. This means, that a ViUR application has to be deployed to a project in the Google Cloud Platform when it is run on the internet.

Before you start your first ViUR project, make sure that at least the first of the following prerequisites are installed on your system.

.. note::
    We strongly recommend to use a POSIX-like operating system like Linux or Mac OS for developing ViUR applications.

    Getting ViUR to run on Microsoft Windows properly is a pain in the ass. The only well-working solution to use a Windows system for ViUR development is when the `Windows Subsystem for Linux <https://en.wikipedia.org/wiki/Windows_Subsystem_for_Linux>`_ is used - otherwise, forget about it.


------------
Python & pip
------------

Since ViUR is a framework written in pure Python, it requires a Python interpreter to be installed. ViUR currently runs with Python 2.7 only, so this must be installed on your system.

.. note::
    A Python 3.7 port of ViUR is under development and will be made available as soon as we do our first experiences with the Python 3 Standard Environment on the Google App Engine.

`Pip <https://pypi.org/project/pip/>`_, the Python package installer, is also a necessary feature to develop applications with ViUR.

----------
gcloud SDK
----------

For the deployment as well as a local development and testing environment, Google offers the `gcloud SDK for Python <https://cloud.google.com/appengine/docs/standard/python/download>`_.

Download and install the gcloud SDK natively from the above location for your platform. Mac OS, Linux and Windows are supported. In case that Linux is used, your favorite package manager should be consulted first, maybe it already supports packages for the gcloud SDK for Python.

.. note::
    Google offers its "Python Standard Environment" that ViUR is using only for Python 2.7 for now.

    They are working on a Python 3 version right now, same as we do with ViUR 3. For now, we have to be
    patient and have to use both the Python 2 Standard Environment and ViUR 2.x framework.

After you successfully installed the gcloud SDK, make sure that you install the following components:

- app-engine-python
- app-engine-python-extras
- cloud-datastore-emulator

To install all required gcloud components, just run

.. code-block:: bash

    gcloud components install app-engine-python app-engine-python-extras cloud-datastore-emulator


---------------------
Further prerequisites
---------------------

For a full ViUR development environment, the following components must also be installed and made available on your system:

- `PyJS <https://github.com/viur-framework/pyjs>`_ is a Python-to-Javascript compiler that we use to compile ViUR's web-based administration interface `vi <https://github.com/viur-framework/vi>`_, which is written in Python. PyJS itself is discontinued, so that we are looking for an alternative, but for now its essentially required.
- `{less} <http://lesscss.org/>`_ is a compiler for a *better* CSS-dialect. It is also required to ViUR's web-based administration interface  **vi** but also by our design- and UI-framework `ignite <https://github.com/viur-framework/ignite>`_
- In most cases it is required to install `npm <https://www.npmjs.com/>`_ to get {less} and build-systems like gulp to work, which is also used by **ignite**.


=======================
Starting a ViUR project
=======================

For a professional project setup, we recommend to use our pre-configured `base repository <https://github.com/viur-framework/base>`_. This repository can be used for a ViUR project setup that imports the required ViUR modules like *server*, *vi* and *ignite* as submodules into the repository, so they can easily be upgraded to newer versions and supplied bugfixes.

Simply clone the base repository and afterwards run ``clean-base.py`` to obtain a stand-alone repository which can immediately be executed or pushed wherever you like.

These are the commands to be executed in a shell:

.. code-block:: bash

   # Clone base repository
   git clone https://github.com/viur-framework/base.git hello-viur

   # Change into folder
   cd hello-viur

   # Run clean-base.py
   python clean-base.py

   # Commit changes done
   git commit -a

   # Run development server
   ./local_run.sh

See the README-file of the repo for further help!

---------------
The first login
---------------

On the first startup, ViUR creates an new admin-user named ``admin@<your-app-id>.appspot.com`` with a random password within the database. This password is printed to the server debug console, where you have to copy it out.

Watch out for a line that looks like this:
::
   ViUR created a new admin-user for you! Username: admin@myapp.appspot.com, Password: SU7juUIb1F2aZ

When the system is started in the cloud for the first time, an e-mail with this password is sent to all application administrators.

Alternatively, you can login with a simulated Google user. Both login forms are provided by the default server and can be done using the *Vi*.

------------
What's next?
------------

When you came to this point, you're ready to start with the :doc:`basic concepts <basics>` and do first steps in developing your project.
