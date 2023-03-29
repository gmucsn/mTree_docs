=================
Quickstart Guide
=================

.. _quickstart_guide:

.. _about_qs_guide:
About this Guide
================

This guide will lead you through the required installations, configurations, and steps to download and use **mTree** on your machine. It 
will also show you the main functionalities of **mTree** and should serve as a jumping-off point for further learning. This guide is meant 
to be understandable to complete beginners, and currently documents processes for Windows and Mac users. **mTree** is however compatible 
with major Linux distributions.

By the end of this **Quickstart Guide** you should be able to:  

* set up mTree on your machine
* download examples 
* run an example simulation
* set up your own mTree project
* implement the main functionalities of mTree
* debug mTree projects
* use the reference guide
* continue learning mTree with further examples.
.. TODO add hyperlinks

.. _setting_up_mtree:
Installation
============
.. Subtitle? Completing this section provides you with the software tools to complete the rest of the guide.
.. TODO think about incorporating the image guide below.

Docker and mTree
----------------

The user version of mTree is distributed as a **Docker** image, so in order to use the latest version of mTree 
you need both Docker and the latest mTree image. **Docker** is a way to package code so that is runs the same way on 
any system, to install it follow this guide: :ref:`install-docker-desk`. The guide specifically shows you how to install 
**Docker Desktop**, which is also used in **mTree** installation and configuration guide.

Once you have **Docker** installed, you can download the latest **mTree** image, following this guide: :ref:`install-mTree`.

.. TODO check if there is some version of Windows on which docker cannot be installed (<10 AFAIK)

Git
---

In order to download the examples used in this guide, you will need git. Even if you are unfamiliar with git, there is a good chance it is 
already installed on your computer. Depending on your operating system, git installation will differ slightly.

.. TODO find a good beginner git guide and recommend it
.. TODO check if you can clone public github repos without a github account ??
.. TODO formatting

*Mac Users*  
    * Open up Terminal and run :code:`git --version`.
    * If the command is not recognized, follow this link to `Download Git for macOS <https://git-scm.com/download/mac>`_. 
    * You have several options on how to install **git**. The **homebrew** route is a good option, for which you can follow this tutorial 
    video: `Git Homebrew Installation <https://www.youtube.com/watch?v=ZM3I16Z-lxI>`_. 
*Windows Users* 
    * Open up Command Prompt or PowerShell and run :code:`git --version`.
    * If the command is not recognized, follow this link to `Download Git for Windows <https://git-scm.com/download/win>`_.
    * And follow this tutorial video `Intall Git for Windows <https://www.youtube.com/watch?v=4xqVv2lTo40>`_.

IDE and Python
--------------

While not strictly required, we using an Integrated Development Environment (IDE) to edit and view **mTree** simulation code. If you are 
unfamiliar with any IDE, `VSCode <https://code.visualstudio.com>`_ and `Spyder <https://docs.spyder-ide.org/3/installation.html>`_ are 
great IDEs for python.

Similarly, installing python natively is not strictly required to be able to run or develop mTree simulations, it is highly recommended 
for unit testing. Get the latest `Python distribution <https://www.python.org/downloads/>`_ or install it with a suite of science-oriented 
packages through `Anaconda <https://www.anaconda.com/products/distribution>`_.

.. _cloning_mTree_auction_examples:

Cloning mTree_auction_examples Folder
==============================

We are going to clone (download a copy) the `mTree_auction_examples <https://github.com/nalinbhatt/mTree_auction_examples.git>`_ repository 
and run one of the examples to make sure **mTree** is running properly on your machine.

Open your **Command Line** (Command Prompt or Power Shell on Windows, Terminal on macOS) at the place in your file system where you would 
like to download the **mTree Examples**. 

.. tip:: 
    If you opened the **Command Line** in a different place, you can navigate your file system using the ``cd`` command. If you are new to 
    **Command Line** you can check out these video tutorials:

    | `Terminal for Beginners <https://medium.com/@grace.m.nolan/terminal-for-beginners-e492ba10902a>`_ (macOS) 
    | `A Beginner's Guide to the Windows Command Prompt <https://www.makeuseof.com/tag/a-beginners-guide-to-the-windows-command-line/>`_ (Windows)

Once at your desired location, run the following code to create a local copy of the **mTree_auction_examples** folder:

.. code-block:: console

    git clone https://github.com/nalinbhatt/mTree_auction_examples.git

.. _running_mTree_auction_examples:

Running an Example 
==================

Because **mTree** is containerized, to run it we need to create a **Docker** container based on the image. This 
is easy using the **Docker Desktop** app that we downloaded in  :doc:`installation` section. 

.. _mTree_auction_examples_container_setup:

Container Setup
---------------

Follow the steps in the :ref:`mTree-container-setup` guide, setting the **Host Path** to your **mTree_auction_example** folder. 

After finishing the setup process, click **Container/Apps** on the sidebar of **Docker Desktop** and select your  **mTree_auction_examples** 
container.

.. figure:: _static/mTree_auction_examples_comp_setup.png
        :align: center

        In your **Containers/Apps** section, you should see a container similar to this with the name you chose.

.. _running_mTree_auction_examples_container:

Running the Container
---------------------

Start the container and open the **Command Line Interface** (**CLI**) from inside your **Docker Desktop** by clicking the **CLI** button. 
A more in-depth look can be found in :ref:`mTree-container-options` under :ref:`mTree-container-start` and :ref:`mTree-container-cli`. 

Your **CLI** should look something like this:

.. figure:: _static/mTree_auction_examples_shell.png
        :align: center

        mTree_auction_examples **CLI** window produced by clicking the **CLI** button.

Double check that the shell is running in the appropriate folder by running the following commands:

*Mac*

.. code-block:: console

    ls 

*Windows*

.. code-block:: console

    dir

You should see the following output:

.. figure:: _static/quick_start_ls.png
        :align: center

        Folders inside mTree_auction_examples.

.. _cva:

Example: Common Value Auction
-----------------------------

One of the subfolders present should have the name **common_value_auction**. Further information about the 
auction style and description can be found here: :ref:`common_value_auction`.

In your **mTree_auction_examples** container **CLI** type in the following command to set 
the current directory to **common_value_auction**.

.. code-block:: console
    
    cd common_value_auction

.. _file_structure:

File Structure
--------------

After setting **common_value_auction** as the current directory, run **ls** (Mac) or **dir** (Windows). You should see the following folders. 

1. :ref:`config <config>`
2. :ref:`mes <Actors>`
3. :ref:`logs <logs>`


.. figure:: _static/quick_start_cva_ls.png
        :align: center

        Folders inside common_value_auction

.. note::
    In order to run an **mTree** simulation, you need to set the current 
    directory to the folder which contains the **config**, **mes**, and **logs** folders.
    **mTree** looks for the config and mes folders in particular to run the simulation. In our example, this 
    folder is called **common_value_auction**.

.. tip:: 
    If you want, you can also set the container's **Host Path** directly to the folder containing the **config** 
    and **mes** folders. You would no longer have to navigate using the CLI but you would need to create a 
    container for each simulation project.

The :ref:`config` folder (short for configurations) contains your configuration files, in a .JSON fomrat which 
describe the way in which your simulation will be run by mTree. The config files describe the types and number 
of actors to be used in the simulation, the number of runs to perform, and allow passing of experimental constants
into the actors.

The **mes** :ref:`mes_folder` folder (short for Microeconomic System) containes the python files where you define the different
:ref:`Actor <Actors>` classes to be used in your microeconomic system. It should contain an :ref:`environment`, 
and at least one :ref:`institution` and :ref:`agent`. 

.. warning:: 

    It is critical that the mTree working directory contains a **config** folder with a **JSON config file** inside
    and a separate **mes** folder with python files inside, containing at least one each of: :ref:`environment` , :ref:`institution` and :ref:`agent`.
    **In the absence of any of these your mTree simulation will not run.**


Inside the **config** folder in the **common_value_auction** auction example, you should see a **basic_simulation.json** file. 
This is the config file which we will run. 

For the next step we want to make sure that our current directory is **common_value_auction** so if you used the **cd** command to 
change the directory to **config** and view its contents, we want to go up a directory using the following command to make sure 
we are in the right directory. 

.. code-block:: console 

    cd .. 

.. _run_config:

Running common_value_auction simulation
------------------------------------------

We can type the following command into the **shell** to start **mTree**.  

.. code-block:: console 

    mTree_runner 

You should see something similar to this.

.. figure:: _static/quick_start_mTree_runner.png
        :align: center

        mTree_runner window

Enter the following to start the selection process for the config file.

.. code-block:: console 

    run_simulation

Your window should look like this. 

.. figure:: _static/quick_start_run_simulation.png
        :align: center

        run_simulation window

Click **<enter>** to select and run the **basic_simulation.json** file. 
Your output should look something similar to this. 

.. figure:: _static/quick_start_run_config.png
        :align: center

        Running basic_simulation.json file 

.. _finished_sim:

How to know your simulation has finished running? 
-------------------------------------------------

mTree provides a ``check_status`` command that allows you to inquire the state of the simulation from the **shell** or **console**. 
Run the following command in your **shell** to see the state of the simulation. If you wish to know more about this command visit :ref:`sim_state` 
section. 


.. code-block:: console

    check_status

.. note:: 

    You can enter the ``check_status`` command multiple times to view the state of your simulation. 

Depending on the when you entered the ``check_status`` command, you should see any one of the following screens. 

.. figure:: _static/quick_start_check_status_running.png
    :align: center

    This indicates our simulation is still running 

.. figure:: _static/quick_start_check_status_finished.png
    :align: center

    This indicates our simulation has finished running and we can move 
    to the next step and view our simulation results. 

Once we have identified that our simulation has finished we can move on to the next step which involves 

.. _sim_results:

Simulation Results
------------------

Ideally when a simulation is run, you should setup :ref:`Actors <Actors>` in such a way that 
they constantly :ref:`log <logs>`  their states to :ref:`.log <log_file>`  and  :ref:`.data <data_file>` files. 
This allows us to analyze how Actors behaved in our system, what decisions they made, and what effects those decisions had on the 
system as whole. 


logs
^^^^
The **logs** folder, inside your simulation folder (which in our case is **common_value_auction**), is where the 
output from your simulation gets stored. You should see a file ending in ``.log`` and a file ending in ``.data``. 

More on how these files are named can be found :ref:`here<log_file>`. 

.. note:: 
    In the figure below, we use `VSCode <https://code.visualstudio.com>`_ to open the generated **log files**. 
    However, no **IDE** is necessary to open these files and your notepad should also work. 
    That being said, we still advise using an **IDE**, like **VSCode**, to interact with an **mTree simulation**, 
    since they make viewing and editing files of different formats more intuitive. 

The first few lines of you ``.log`` file document the config file parameters which were used to run the simulation

.. figure:: _static/quick_start_log_config.png
        :align: center

        basic_simulation-2022_02_28-09_32_04_PM-R1-experiment.log


The rest of your ``.log`` file should look as follows. 

.. figure:: _static/quick_start_log_rest.png
        :align: center

        basic_simulation-2022_02_28-09_32_04_PM-R1-experiment.log


Your ``.data``  file should look something like this - 

.. figure:: _static/quick_start_data_log.png
        :align: center

        basic_simulation-2022_02_28-09_32_04_PM-R1-experiment.data


.. note:: 

    Don't worry if the log files on your end don't match the ones shown here word for word. Since **mTree** is a 
    concurrent Agent-Based Modelling software, it is common for different :ref:`Actors <Actors>` to log asynchronously to the
    same ``.log`` and ``.data`` files, giving them an out of order look. 
    
.. _check_errors:

Checking for Errors
-------------------

You can use the ``ctrl F`` (Windows) or  ``cmd F`` (Mac) command to search for ``Error`` messages in the ``.log`` file. If there are no results then it is likely 
that your simulation has run properly. If there are instances of ``Error`` messages then check out the :ref:`error` section.

.. warning::

    If you see no results for ``Error`` but your mTree log stops logging in the middle of the simulation, then it is still 
    possible you have logic errors that don't terminate the process. Luckily, you don't have to worry about that in the 
    **common_value_auction** auction example.

.. _quitting:

Quitting
--------

Once the simulation has ended, you can run ``quit`` command in the **docker shell** to kill mTree. The ``quit`` command 
is used to kill all mTree processes as well as **delete** all :ref:`Actor <Actors>` instances previously created to run the simulation. 

.. code-block:: console 

    quit

Your console should look like some version of this - 

.. figure:: _static/quick_start_quitting_mTree.png
        :align: center

        Quitting **mTree**
        
.. _conclusion:

Conclusion
----------

.. TODO: Revise this conclusion to link to the new pages
Congratulations on successfully running your first mTree simulation! If you want to know how this example was built
or you want to find more projects like this, checkout :ref:`common_value_auction` or :doc:`learning_paths` sections. 
If you want to view a more in-depth case which builds an mTree project from scratch, checkout :doc:`quick_build`. 

.. TODO add a section similat to https://econwillow.sourceforge.net/manual.html#_lesson_0_wherein_we_install_willow
.. TODO add section similar to https://docs.google.com/document/d/1kFkMUeHiWZ2PZgZXWYhMYC_AAv1BMN80_WOVxDVY3Sg/edit
































