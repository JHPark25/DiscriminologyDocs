Backend
=============
.. toctree::
   :maxdepth: 1

   Installation
   Admin Panel
   Database Structure
   API Server
   Other Files

#############
Installation
#############
To run this project, make sure node.js is installed. Then, run ``npm install``
in the ``backend`` directory. To run the API server, run the following.

::

    cd server; node app.js

To run the admin panel, run the following in a different terminal window.

::

    cd admin; node admin.js 


#############
Admin Panel
#############

The admin panel is for Discriminology staff to interact with the database
through a graphical interface. All the code is contained within the
``backend/admin`` folder. Currently, there is only one user with access to the
admin panel. However, with that account, more accounts can be added by adding to
the ``admin_users`` table in the admin panel.

The ``dashboard.tsx`` file is the TypeScript file that renders the homepage of
the admin panel. Here, the boxes that are displayed for each of the tables are
compiled.

The ``admin.js`` file contains the heart of the admin panel. The admin panel
runs on an Express app at a desired port. At the
`top <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/backend/admin/admin.js#L18>`_,
we import the objects for all the tables in our database. Then, we initialize
the admin panel. Currently, we have three groups of `links <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/backend/admin/admin.js#L30>`_,
the ``reportsNavigation``, ``schoolsNavigation``, and ``userNavigation``. The
`translations <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/backend/admin/admin.js#L53>`_
can be used to change the names for the columns of the table when
they are displayed on the admin panel. This will not affect the names as they
are stored in the database. Each of the tables is a "resource", and we order the
columns within the resource's `properties <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/backend/admin/admin.js#L120>`_.
Finally, we define the `login <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/backend/admin/admin.js#L409>`_
method for logging in to the admin panel. The method calls the backend to see if
the username and password is valid.

#############
Database Structure
#############

#############
API Server
#############

This portion of the code is under the ``backend/server`` directory. It contains
the code for the server that the frontend and admin panel makes requests to.
Within the folder, there is a ``public`` directory, which cotanins images used
throughout the site, and the ``app.js`` file, which contains all the backend
endpoints.

The backend is built on the Express framework. ``app.js`` is separated into GET
and POST requests. A status code of 200 is returned for requests that succeed,
and 400 is returned for failed requests.

*************
GET Requests
*************

+++++++++++++
/questions
+++++++++++++

`This endpoint <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/backend/server/app.js#L35>`_
returns the questions for a given category. The category is one of the
parameters in the endpoint. Thus, ``/questions?category=suspension`` will return
the questions for the suspension category. The response is the status code, the
questions, given in a list, and the error, if applicable.

+++++++++++++
/names
+++++++++++++

`This endpoint <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/backend/server/app.js#L53>`_
returns the IDs and names for all the entries in a given table in the database.
The table name is one of the parameters in the endpoint. Thus,
``/names?type=tags`` will return the IDs and names of all the tags. Note that
the number of entries will be limited to 26,000, since large amounts of data
will make the backend unresponsive. The upper bound can be changed via the
``maxEntries`` global variable found `here <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/backend/server/app.js#L51>`_.
In the frontend, we also limit the number of schools shown, so the page is not
overwhelmed. Therefore, all the schools will not show up inside the dropdown
menus. The response is the status code, the entries, given as a list, and the
error, if applicable.

+++++++++++++
/schools
+++++++++++++

`This endpoint <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/backend/server/app.js#L70>`_
returns the name, city, and state of a school, given a school ID. The school ID
is one of the parameters in the endpoint. Thus, ``/schools?id=1`` will return
the information for the school with ID of 1. The response is the status code,
the entries that match the ID, given as a list, and the error, if applicable.

+++++++++++++
/tli-tags
+++++++++++++

`This endpoint <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/backend/server/app.js#L84>`_
returns the most frequently used tag for a given school. The most frequently
used tag is the tag that is selected the most, summed over all categories. The
school ID is one of the parameters in the endpoint. Thus, ``/tli-tags?id=1``
will return the most frequently used tag for the school with ID of 1, which is
the default school. The categories that it will loop over are defined
`here <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/backend/server/app.js#L32>`_
and can be freely changed as more categories are added. The response is the
status code, the name of the tag, and the error, if applicable.

+++++++++++++
/tli-tags-all
+++++++++++++

`This endpoint <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/backend/server/app.js#L123>`_
returns the most frequently used tag in the last week. The response is the
status code, the name of the tag, and the error, if applicable.

*************
POST Requests
*************

+++++++++++++
/register
+++++++++++++

`This endpoint <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/backend/server/app.js#L161>`_
adds a new user to the database given their registration credentials. The input
is of the following form.

::

    {
        username: 'test_username',
        email: 'test_email',
        city: 'Cambridge',
        state: 'Massachusetts',
        zipCode: '02138',
        organization: 1
    }

The response is the status code and the error, if applicable.

+++++++++++++
/user
+++++++++++++

`This endpoint <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/backend/server/app.js#L185>`_
gets the ID for a given user's username. The input is of the following form.

::

    {
        username: 'test_username'
    }

The response is the status code, the ID, and the error, if applicable.

+++++++++++++
/admin-user
+++++++++++++

`This endpoint <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/backend/server/app.js#L201>`_
checks that a given email and password is valid for admin users. This endpoint
is used when signing in on the admin panel. The input is of the following form.

::

    {
        email: 'test_email',
        password: 'test_password'
    }

The response is the status code, the number of matching entries with such email
and password, and the error, if applicable.

+++++++++++++
/responses
+++++++++++++

`This endpoint <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/backend/server/app.js#L217>`_
stores the given responses to a report in the database. This endpoint is used
for adding new reports to the database. The input is of the following form.

::

    {
        category: 'suspension,
        answers: ['answer1', 'answer2', 'answer3'],
        question_no: 3,
        tags: 'tags',
        date: '2022/12/23'
    }

The response is the status code and the error, if applicable.

+++++++++++++
/schools
+++++++++++++

`This endpoint <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/backend/server/app.js#L246>`_
stores a new school request in the database. This endpoint is used when users
use the modal to request a new school. The input is of the following form.

::

    {
        name: 'name',
        city: 'city',
        state: 'state'
    }

The response is the status code and the error, if applicable.

+++++++++++++
/tli-reports
+++++++++++++

`This endpoint <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/backend/server/app.js#L264>`_
gets the top level insights for the number of reports for a given
category during a given time period, given a school ID. The input is of the
following form.

::

    {
        id: 1,
        type: 'suspension',
        length: 12,
        duration: 'months'
    }

The response returns the total number of reports for that category in the time
period, as well as the a list that contains the number of reports in each
time interval.

#############
Other Files
#############
All environment variables are stored in the ``.env`` file. Here, we store what
ports the admin panel and the backend server will run on, as well as the
credentials for connecting to the AWS database.

The dependencies are all stored in ``package.json`` and ``package-lock.json``.
