Updates
=============
.. toctree::
   :maxdepth: 1

   Add Questions
   Add Categories

This file will explain what is needed to make some changes that Discriminology
will likely need to make.

#############
Add Questions
#############

To add questions, the questions can be added in the admin panel. To see a
description of each of the fields, see the ``Question`` component in the
frontend, `here <https://discriminologydocs.readthedocs.io/en/latest/frontend.html#question>`_.

The rest of the site should be responsive to the number of questions inputted in
the database and update accordingly.

#############
Add Categories
#############

To add a new category, follow these steps.

1. Create a new reports page for the new category, by following the link `here <https://discriminologydocs.readthedocs.io/en/latest/frontend.html#report>`_.

2. Add a new category to the Reports by Category Chart, following the instructions
`here <https://discriminologydocs.readthedocs.io/en/latest/frontend.html#reportsbycategorychart>`_.
This will add the doughnut chart seen on the Top Level Insights page.

3. Add a new category to the Reports Over Time Chart, following the instructions
`here <https://discriminologydocs.readthedocs.io/en/latest/frontend.html#reportsovertimechart>`_.
This will add the line chart seen on the Top Level Insights page.

4. Add a new button to the Choose Report page, ``frontend/src/pages/choosereport.js``
that allows users to select the new category for a new report being filed.

5. In the admin panel, add to the "questions" table with the new set of
questions and new category.
