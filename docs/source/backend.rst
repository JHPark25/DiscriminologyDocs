Backend
=============
.. toctree::
   :maxdepth: 1

   Installation
   Admin Panel
   API Server
   Other Files

#############
Installation
#############
To run project, make sure node.js is installed. Then, run ``npm install`` in the
``backend`` directory. To run the API server, run the following.

::

    cd server; node app.js

To run the admin panel, run the following.

::

    cd admin; node admin.js 


#############
Admin Panel
#############

The admin panel is for Discriminology staff to interact with the database
through a graphical interface. All the code is contained within the ``admin``
folder.

The ``dashboard.tsx`` file is the TypeScript file that renders the homepage of
the admin panel. Here, the boxes that are displayed for each of the tables are
compiled.

The ``admin.js`` file contains the heart of the admin panel. The admin panel
runs on an Express app at a desired port. At the
`top <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/3f149a40e7e035276b9f4c190426d3491e8bea39/backend/admin/admin.js#L18>`_,
we import the objects for all the tables our database, which are explained more
deeply below. Then, we initialize the admin panel. Currently, we have three
groups of `links <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/3f149a40e7e035276b9f4c190426d3491e8bea39/backend/admin/admin.js#L30>`_,
the ``reportsNavigation``, ``schoolsNavigation``, and ``userNavigation``. The
`translations <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/3f149a40e7e035276b9f4c190426d3491e8bea39/backend/admin/admin.js#L53>`_
can be used to change the names for the columns of the table when
they are displayed on the admin panel. This will not affect the names as they
are stored in the database. Each of the tables is a "resource", and we order the
columns within the resource's `properties <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/3f149a40e7e035276b9f4c190426d3491e8bea39/backend/admin/admin.js#L120>`_.
Finally, we define the `login <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/3f149a40e7e035276b9f4c190426d3491e8bea39/backend/admin/admin.js#L409>`_
method for logging in to the admin panel. The method calls the backend to see if
the username and password is valid.

#############
API Server
#############

This portion of the code is under the ``server`` directory. It contains the code
for the server that the frontend and admin panel makes requests to. Within the
folder, there is a ``public`` directory, which cotanins images used, and the
``app.js`` file, which contains all the backend endpoints.

The backend uses the Express framework. The file is separated into get and post
requests. A status code of 200 is returned for requests that are a success, and
400 is returned for failed requests.

*************
GET Requests
*************

+++++++++++++
/questions
+++++++++++++

+++++++++++++
/names
+++++++++++++

+++++++++++++
/schools
+++++++++++++

+++++++++++++
/tli-tags
+++++++++++++

+++++++++++++
/tli-tags-all
+++++++++++++

*************
POST Requests
*************

+++++++++++++
/register
+++++++++++++

+++++++++++++
/user
+++++++++++++

+++++++++++++
/admin-user
+++++++++++++

+++++++++++++
/responses
+++++++++++++

+++++++++++++
/schools
+++++++++++++

+++++++++++++
/tli-reports
+++++++++++++

`This endpoint <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/3f149a40e7e035276b9f4c190426d3491e8bea39/backend/server/app.js#L261>`_
gets the top level insights for the number of reports for a given
category during a given time period. The input is of the following form.

::

    {
        id: 1,
        type: 'suspension',
        length: 12,
        duration: 'months'
    }

The response returns the total number of reports in the time period, as well as
the a list that contains the number of reports in each duration.

#############
Other Files
#############
All environment variables are stored in the ``.env`` file. Here, we store what
ports the admin panel and the backend server will run on, as well as the
credentials for connecting to the AWS database.

The dependencies are all stored in ``package.json`` and ``package-lock.json``.
