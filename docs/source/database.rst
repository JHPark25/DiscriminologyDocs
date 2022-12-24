Database
=============
.. toctree::
   :maxdepth: 1

   Viewing
   Tables

#############
Viewing
#############

To view the database, you can use the admin panel. If you would like a more
comprehensive view of the database that can run SQL queries, you can use a
database-viewing program, like pgAdmin4.

#############
Tables
#############

All the tables will contain an ``id`` column, which is an integer that
auto-increments and serves as the primary key. They will also contian a
``createdAt`` and ``updatedAt`` column, which default to the
``CURRENT_TIMESTAMP``. These are solely for the purposes of the admin panel and
are not used anywhere else.

*************
questions
*************

The ``questions`` table contains the following.

* ``question`` for the text of the question.
* ``question_type`` for the type of the question ("radio", "checkbox", "text-field").
* ``category`` for the category of the question ("policing", "suspension").
* ``options`` for the options only for multiple choice questions. Options are separated by a `` && " delimiter.
* ``textfield_label`` for the label of the textfield for free response questions.

*************
reports
*************

The two reports tables (``suspension_reports`` and ``policing_reports``) table
contain the following columns.

* ``school_id``, which is a foreign key to the school ID column. This stores the school that the report is for.
* ``user_id``, which is a foreign key to the user ID column. This stores the user that made the report.
* ``tags`` for storing all the tags clicked. Tags are separated by a `` && " delimiter.
* ``date`` for the date of the incident. This is the field used for top level insights, not the ``createdAt`` column.
* ``question?`` for the response to each question

*************
users
*************

This table stores information about credentials to the app itself. Initially,
there is one guest user and two T4SG users.

* ``username`` for the username.
* ``email`` for the email.
* ``organization_id``, which is a foreign key to the organization ID column. This stores the organization the user is affiliated with.
* ``city`` for the city.
* ``state`` for the state.
* ``zip`` for the ZIP.

*************
admin_users
*************

This table stores information about credentials to the admin panel. Initially,
there is only one user.

* ``email`` for the email of the user.
* ``password`` for the password.

*************
organizations
*************

This table stores the names of all the organizations. There is a default
organization that is initialized to have ID of 1.

* ``name`` for the name of the organization.

*************
schools
*************

This table stores all the information about registered schools.

* ``name`` for the name of the school.
* ``address`` for the address.
* ``city`` for the city.
* ``state`` for the state.
* ``zip`` for the ZIP.
* ``level`` for the level of school (Elementary, Middle, High School).

*************
requests
*************

This table stores all the information about requested schools that are waiting
to be added.

* ``name`` for the name of the school.
* ``city`` for the city.
* ``state`` for the state.

*************
tags
*************

This table stores all the tags for the report pages. Some pre-defined tags
are already loaded into the database.

* ``name`` for the name of the tags.
