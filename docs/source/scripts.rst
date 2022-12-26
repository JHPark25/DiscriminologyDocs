Scripts
=============
.. toctree::
   :maxdepth: 1

   Installation
   Programs
   Other Files

#############
Installation
#############
To run the scripts, make sure python is installed. Then, run
``pip install -r requirements.txt`` in the ``scripts`` directory to install all
dependencies. To run any of the programs, run the following command:

::

    python FILE.py

where FILE.py is the name of the file that should be run. Some of the programs
may take some time to run because they are transferring large amount of data.

#############
Programs
#############

*************
add-reports.py
*************

This `program <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/scripts/add-reports.py>`_
inserts random data for reports for the sample school (school ID of 1) that we
have initialized for demonstration purposes. This is so that the top-level
insights will display data for the "Test School". It is unlikely that you will
need to re-run this script, since any new reports will automatically be
displayed in the top-level insights.

The scripts selects a random tag and a random category and submits 0 to 5
reports for roughly each day of the 2022 calendar year.

*************
categories.py
*************

This `program <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/scripts/categories.py>`_
loads the two initial categories, suspension and policing/security, along with
the color scheme that we chose for the graphs.

*************
questions.py
*************

This `program <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/scripts/questions.py>`_
inserts all the questions into the database. It is unlikely that you will need
to re-run this script, since any additional questions can be added via the admin
panel. The questions are defined as constants `here <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/scripts/questions.py#L20>`_.

Note that the associated IDs for each category is pre-defined `here <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/scripts/questions.py#L15>`_,
so if the mapping between IDs and categories changes, this global variable
should be updated.

*************
reports.py
*************

This `program <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/scripts/reports.py>`_
adds the necessary response columns associated with each question of the report.
This can be used to add columns to the ``reports`` tables, when new questions
are added. Before running the program, the ``question_start`` and
``question_end`` global variables should be adjusted `here <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/b3808780e76bd9cc0392cad8d8df90fc6574f5e3/scripts/reports.py#L13>`_.
Columns will be added for question numbers from ``question_start`` through
``question_end``. For example, if there are four existing questions and two more
are to be added, then ``question_start = 5`` and ``question_end = 6`` will add
the two columns for the two new questions.

Note that columns should only be added when the maximum number of questions in a
category changes. Since reports from all cateogires are stored in the
``reports`` table, there just needs to be enough columns for the category with
the largest number of questions. Currently, both suspension and policing reports
have a total of 8 questions. Thus, there are columns for ``question1`` through
``question8``.

*************
schools.py
*************

This `program <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/scripts/schools.py>`_
takes the schools from the previous database and inserts them into the new
database.

For the state ID, we use the global ``states`` variable, defined `here <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/scripts/schools.py#L19>`_
to map the state to the ID. If the mapping of ID to state/territories changes,
this global variable should be updated. However, this will probably be unlikely
because we have already loaded in the states/territories into the ``states``
table.

*************
states.py
*************

This `program <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/scripts/states.py>`_
was used to insert the states and territories of the US into the database. It is
unlikely that you will need to re-run this script, since they should all already
be in the database under the ``states`` table.

*************
tags.py
*************

This `program <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/scripts/tags.py>`_
inserts the pre-defined tag names into database. It is unlikely that you will
need to re-run this script, since they should all be in the database
under the ``tags`` table. Any additional tags can be added through the admin
panel.

#############
Other Files
#############
All environment variables are stored in the ``.env`` file. Here, we store the
credentials for connecting to the current AWS database, as well as the previous
one, so that we can transfer the schools.

The dependencies are all stored in ``requirements.txt``.
