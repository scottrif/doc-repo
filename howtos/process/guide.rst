.. _guide:

Template Setup Guide
####################

Follow the instructions below to go from nothing to a robust documentation
framework hosted on GitHub, including an existing workflow for managing
community contributions that can scale with your project.

Overview
========
This documentation project is built on Sphinx, which relies on Python and
reStructuredText. It uses files and directories for content and strucutre to
generate a static HTML website. reStructuredText is a highly readable markup
language with powerful organizational and layout capabilities. 

Deploying this template for your Open Source project works best in a Linux
based operating system, though it can be done from Windows with a little
additional effort. At the very least, you will need a basic knowledge of Git
and the bash command line. You can find an introduction to Git and the
GitHub workflow in our :ref:`doc_gen`.

This guide assumes that you have already received approval for your Open
Source project and that your Intel sponsored GitHub project exists. If not,
please see the prework below.

Prework
-------

* Open source approval process: 
  https://opensource.intel.com/how-to/open-source-approval-process 

* Open source whitelist process: 
  https://opensource.intel.com/how-to/open-source-whitelist-process

* Open source development model:
  https://opensource.intel.com/how-to/open-source-intel-open-source-development-model

* Request a GitHub project under Intel sponsorship:
  https://opensource.intel.com/how-to/otc-infrastructure/github

Setup Steps
===========
#. Set up a GitHub.com documentation repository.
#. Retrieve the document template as a zip file from https://github.intel.com/otc-tcs/documentation-template.
#. Extract document template to a directory and push it to your GitHub.com
   documenation repository: https://help.github.com/articles/adding-an-existing-project-to-github-using-the-command-line/.
#. Create a directory called ``website`` at the same level where the repo
   was extracted. This will be the target for the ``make publish`` command
   later. The final directory structure should look like this:

   .. code-block:: bash

      <projectname>/
         doc-repo
         website

#. Set up a GitHub pages repository for your organization
   called ``<projectname>.github.io``. Add a file called ``.nojekyll``
   to top level of your GitHub pages repo rather than ``README.md`` to make
   sure HTML is rendered correctly.
#. ``git clone`` the GitHub pages repository to your ``website`` directory.
#. Make sure the master branch of the github.io repo has github pages
   publishing enabled. There can be only one.
#. For building and deployment instrucions go to our :ref:`doc_gen`. 
#. TOC trees need to be in the index.rst at each level to define the
   site structure. For example, this is the TOC tree used to generate
   this site:

   .. code-block:: rest

      .. toctree::
         :maxdepth: 1

         introduction/index.rst
         getting_started/index.rst
         release_notes.rst
         howtos/index.rst
         contribute/index.rst

#. Changes to theme can be made by editing ``static/custom.css``.
#. No matter where the images are before the build, after the build all the
   images are collected in one directory: all the image filenames must be
   unique.
#. Modify ``conf.py`` to reflect your project:
  
   .. code-block:: bash
   
      # General information about the project.
      project = u'<project name>'
      copyright = u'<year>, <project name>'
      author = u'<project name> developers'

#. Modify ``substitutions.txt`` to reflect your project:

   .. code-block:: rest

      .. |PN| replace:: <project name>

      .. |LPN| replace:: <long project name>

      .. _project repo: https://github.com/<projectname>/

      .. _documentation repo: https://github.com/<proejctname>/<docrepo>

      .. _documentation site: https://<projectname>.github.io

      .. _project website: https://github.intel.com/pages/otc-tcs

#. Edit ``LICENSE`` to reflect your project name and requirements
#. Make any edits to ``Makefile`` that might be needed to facilitate the
   build or change the name of your local instantiation of the github.io
   website repository directory.
#. Replace logos and favicon in ``/images`` with your project logos
#. Run ``make clean`` to remove any previously generated HTML.
#. Regenerate the HTML with Sphinx with ``make html``. 
#. Push the updated content to the github.io repo with ``make publish``.
