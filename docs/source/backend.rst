Backend
=============
.. contents::

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

+++++++++++++
Section 1 Title
+++++++++++++


Other Files
######################################
All environment variables are stored in the ``.env`` file. Here, we store what
ports the admin panel and the backend server will run on, as well as the
credentials for connecting to the AWS database.

The dependencies are all stored in ``package.json`` and ``package-lock.json``.
