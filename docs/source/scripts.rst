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
``pip install -r requirements.txt`` in the ``scripts`` directory. To run any of
the programs, run the following command:

::

    python FILE.py

where FILE.py is the name of the file that should be run.

#############
Programs
#############

*************
add-reports.py
*************

This `program <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/b3808780e76bd9cc0392cad8d8df90fc6574f5e3/scripts/schools.py#L20>`_
inserts random data for reports for the sample school that we have initialized.
This is so that the top-level insights will display data. It is unlikely that
you will need to re-run this script, since any new reports will automatically
be displayed in the top-level insights.

*************
questions.py
*************

This `program <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/b3808780e76bd9cc0392cad8d8df90fc6574f5e3/scripts/schools.py#L20>`_
inserts the questions into the database. It is unlikely that you will need to
re-run this script, since any additional questions can be added via the admin
panel.

*************
reports.py
*************

This `program <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/b3808780e76bd9cc0392cad8d8df90fc6574f5e3/scripts/reports.py#L18>`_
adds the necessary columns for each question of the report. This can be used to
add columns to the reports tables, when new questions are added. Before running
the program, the ``question_start`` and ``question_end`` global variables should
be adjusted `here <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/b3808780e76bd9cc0392cad8d8df90fc6574f5e3/scripts/reports.py#L13>`_.
Columns will be added for question numbers from ``question_start`` through
``question_end``. For example, if there are four existing questions and two more
are to be added, then ``question_start = 5`` and ``question_end = 6`` will add
two columns for the two new questions.

*************
schools.py
*************

This `program <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/b3808780e76bd9cc0392cad8d8df90fc6574f5e3/scripts/schools.py#L20>`_
takes the schools from the previous database and inserts them into the new
database.

*************
states.py
*************

This `program <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/b3808780e76bd9cc0392cad8d8df90fc6574f5e3/scripts/states.py#L233>`_
was used to insert the states and territories of the US into the database. It is
unlikely that you will need to re-run this script, since they should all already
be in the database under the ``states`` table.

*************
tags.py
*************

This `program <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/b3808780e76bd9cc0392cad8d8df90fc6574f5e3/scripts/tags.py#L28>`_
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
