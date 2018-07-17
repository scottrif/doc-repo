.. _pandocs-conversion:

Pandocs Conversion Tutorial
###########################

.. contents:: :local: 
   :depth: 2


This tutorial shows you how to use ``pandoc`` to convert files in various 
formats. 

Table 1 shows current conversions. 

.. list-table:: Table 1. Conversions
   :widths: 80 100 100
   :header-rows: 1
   :stub-columns: 1

   * - Convert
     - From
     - To
   * - reSTructured Text to HTML
     - ``.rst``
     - ``.html``
   * - Markdown to reSTructured Text 
     - ``.md``
     - ``.rst``
   * - reSTructured Text to HTML  
     - ``.rst``
     - ``.html``

Scope
=====

Conversion should be a preliminary step in migrating to Sphinx 
for your documentation project. The results of conversion will complete
about 80% of the work. It's expected that you'll edit converted files as 
post-processing. We recommend studying the `Pandoc website`_ to learn more. 

In the Clear Linux\* documention, we established 
`Documentation Contribution Guidelines`_, which explain conventions and 
usage of reST syntax. We encourage you to establish similar guidelines for 
your team. Even minimal initial investment in guidelines greatly 
reduces future work. More importantly, providing clear guidelines supports 
your team's long-term maintence efforts. 

Note: See also the Clear Linux `reSTructured Text Guide`_. 

Prerequisites 
=============

* `Install Pandocs`_
* Command line interface basic skills
* Text editor (e.g., Sublime, Notepad++, etc.)
* Web browser

Introduction
============
We recommend following reST conventions and best practices for Sphinx. To 
learn more, visit the `Sphinx website`_

#. To get started, vist the `pandocs-tutorial repo`_. 
    
#. On your host machine, clone the files in the latter directory. 

   .. code-block:: bash

      $ git clone git@github.intel.com:OTC-TCS/pandocs-tutorial.git

#. Navigate to the cloned directory with your CLI. 
   
   .. code-block:: bash

      $ cd pandocs-tutorial

   .. note:: 

      You do not need to initialize this directory for Git or set up a remote. 

#. In your text editor, view the files. They are now in a finished state. 


#. Remove **only** two documents with the ``.html`` and ``.rst`` formats. 
   
   .. code-block:: bash

      rm *.html 

   .. code-block:: bash    

      rm *.rst

   .. note:: 

      **Do not** remove the bash scripts--with ``.sh`` format.   

Single file Conversion
=======================

For single file conversions, 


cd into the file directory:

.. code-block:: bash

   $ cd pandocs-tutorial


From Markdown to reST
---------------------

#. Run the command: 

.. code-block:: bash

   $ pandoc --from=markdown --to=rst --output=cicero.rst cicero.md

From Markdown to HTML
---------------------

#. Run the command: 

.. code-block:: bash

   $ pandoc cicero.md -f markdown -t html -s -o cicero.html

From reST to HTML
-----------------
#. Run the command: 

.. code-block:: bash

   $ pandoc -f rst -t html cicero.rst > cicero.html

Multiple file Conversion using Pandoc
=====================================

You will learn how to convert multiple files simultaneously.

#. Navigate to the cloned directory with your CLI. 
   
   .. code-block:: bash

      $ cd pandocs-tutorial

#. Add two more files of the following file formats to this directory. 
   
   *  ``.rst``
   *  ``.html``
   *  ``.md``
   
Now you will convert multiple files at a time using a bash script. 

.. note:: 
      
   In the CLI output, the conversion is shown in process. 

From Markdown to reST
---------------------

#. To convert multiple ``.md`` files to ``.rst``, run: 

   .. code-block:: bash

      ./md2rst.sh

From Markdown to HTML
---------------------

#. To convert multiple ``.md`` files to ``.html``, run: 

   .. code-block:: bash

      ./md2html.sh

From reST to HTML
---------------------

#. To convert multiple ``.rst`` files to ``.html``, run: 

   .. code-block:: bash

      ./rst2html.sh


**Congratulations!** You have learned how to convert single files and
multiple files to your preferred format. 


.. _pandocs-tutorial repo: https://github.intel.com/OTC-TCS/pandocs-tutorial

.. _Install Pandocs: https://pandoc.org/installing.html

.. _Sphinx website: http://www.sphinx-doc.org/en/master/index.html

.. _Pandoc website: https://pandoc.org/

.. _Documentation Contribution Guidelines: https://clearlinux.org/documentation/clear-linux/reference/collaboration/documentation

.. _reSTructured Text Guide: https://clearlinux.org/documentation/clear-linux/reference/collaboration/documentation/rest#additional-information
