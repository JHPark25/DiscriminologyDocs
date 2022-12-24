Frontend
=============
.. toctree::
   :maxdepth: 1

   Installation
   Components
   Pages
   Other Files

#############
Installation
#############
To run project, make sure npm is installed. Then, install all node modules by
running the following.

``` 
npm install
```

Then, to run the frotend, you can run

``` 
npm run start
```

which will redirect you to the homepage. To view it in a mobile view, feel free
to use any mobile-viewing extension, like MobileView in VS Code.

#############
Components
#############

The following components serve as building blocks for the pages that we will
explain later. They can be reused in new pages to keep the styling and
functionality the same. These will be located in the ``src/components`` folder.

*************
CreateReport
*************

*************
Date
*************

*************
Dropdown
*************

*************
Error
*************

*************
Footer
*************

*************
Header
*************

*************
NewSchool
*************

*************
Question
*************

*************
Report
*************

*************
ReportHeader
*************

*************
ReportsByCategoryChart
*************

*************
ReportsOverTimeChart
*************

*************
Tags
*************

#############
Pages
#############

*************
ChooseReport
*************

*************
ForgotPassword
*************

*************
Homepage
*************

*************
Login
*************

*************
Policing
*************

*************
Registration
*************

*************
Suspension
*************

*************
TopLevelInsights
*************

*************
Welcome
*************

#############
Other Files
#############
All environment variables are stored in the ``.env`` file. Here, we store the
API endpoint for the backend, so that when the server that the backend is
located on changes, all endpoints will automatically update.

The dependencies are all stored in ``package.json`` and ``package-lock.json``.

In the ``public`` directory, you will find the logo used for the site, as well
as the base ``index.html`` file.

In the ``src`` directory, you will also find all the styling used in the
``styles`` directory, divided by components and pages. The driver components is
located in ``App.js``, which contains the routes to all the pages that we have
defined. This component is initialized in the ``index.js`` file.
