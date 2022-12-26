Updates
=============
.. toctree::
   :maxdepth: 1

   Add Questions
   Add Categories

This file will explain what changes Discriminology will likely need to make to
support new features.

#############
Add Questions
#############

To add questions, the questions can be added in the admin panel. To see a
description of each of the fields, see the ``Question`` component in the
frontend, `here <https://discriminologydocs.readthedocs.io/en/latest/frontend.html#question>`_.

The rest of the site should be responsive to the number of questions in the
database and update accordingly.

#############
Add Categories
#############

To add a new category, simply add the category in the admin panel to the
``categories`` table, using `this <https://discriminologydocs.readthedocs.io/en/latest/database.html#categories>`_
for reference. The app should automatically react to the new category and
display a new option when choosing reports. Furthermore, the top level insights
page will automatically be updated.
