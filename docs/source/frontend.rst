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

::
    npm install

Then, to run the frotend, you can run

::
    npm run start

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

The `CreateReport component <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/frontend/src/components/createreport.js#L6>`_
renders multiple questions at once so you do not need to call the question
component many times to create a report page.

The ``CreateReport`` component accepts the following props: ``questions``,
``handleMCQChange``, and the ``handleResponseChange``. Using the information
passed through the ``questions`` prop, the ``CreateReport`` component repeatedly
calls the ``Question`` component to generate a form. The ``questions`` prop is
an array of objects that contains an ``id``, ``question``, ``options``,
``question_type``, and ``textfield_label``. See the ``Question`` component for
more information on these.

*************
Date
*************

The `Date component <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/frontend/src/components/date.js#L6>`_
renders a date question. The user can specify a date using a textbox or
selecting a date on a calendar pop-up.

The ``Date`` component accepts ``value`` and ``onChange`` props. The ``value``
defines the date displayed in the date component. ``value`` should be a
``dayjs`` object. ``onChange`` is the function passed down from the parent that
collects the user's response.


*************
Dropdown
*************

The `Dropdown component <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/frontend/src/components/dropdown.js#L6>`_
creates all the dropdown menus in the app. Given the name of a table, this
component loads all the entries in that table.

The ``Dropdown`` component takes the following props: ``table``, ``name``,
``width``, and ``handleChange``. ``table`` is the name of the table to be
queried. ``name`` is the name that should be displayed as the default text.
``width`` defines the width of the dropdown menu. Finally, ``handleChange`` is
the function passed down from the parent component to handle changes to the
value of the dropdown.

::

    <Dropdown
        table="states"
        name="State"
        width="85%"
        handleChange={ onStateChange }
    />

*************
Error
*************

The `Error component <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/frontend/src/components/error.js#L3>`_
is used to display the error messages for invalid inputs. For example, it is
used in the registration page when the confirmation password does not match.

The only prop to the ``Error`` component is the ``message`` that you want to be
displayed as a string.

*************
Footer
*************

The `Footer componet <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/frontend/src/components/footer.js#L6>`_
displays the footer on the bottom of each of the pages. It contains two buttons:
one that takes the user to the homepage and another that takes the user to a new
report page.

*************
Header
*************

The `Header component <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/frontend/src/components/header.js#L3>`_ generates a header that is used at the top of many
pages. The ``Header`` component accepts a ``header`` prop, which is the string
that should be in the header.

*************
NewSchool
*************

The `NewSchool component <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/frontend/src/components/newschool.js#L22>`_
is a modal that allows users to add a new school. Once the button is clicked, a
modal will pop-up and allow users to enter the information for a new school.
Then, upon submitting, a nested modal will appear to confirm the submission.
From there, the user can return to the home page.

*************
Question
*************

The `Question component <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/frontend/src/components/question.js#L7>`_
renders a report question as specified by multiple props on the frontend. The
component can handle MCQ questions (both multiple select and single select MCQ
questions) and textfield questions.

The question component accepts the following props: ``id``, ``question``,
``choices``, ``questionType``, ``textfieldLabel``, ``handleMCQChange``, and
``handleResponseChange``.

``id`` is the unique ID of the question as an integer.

``question`` is required and specifies the question that is rendered. It should
be a string that defines the question's text itself (e.g. “Who are you?“).

``questionType`` defines what kind of question it is and should be defined as a
string amongst the following options: "checkbox", "radio", or "text-field". 
Checkbox and radio are both MCQ style questions, but checkboxes allow for
multiple choices to be selected whereas radio only allows for one choice to be
selected. Textfield is a free response text question.

``choices`` should only be included for MCQ questions and should be an array of
options for the MCQ question (e.g. [“Yes”, “No”, “Maybe”]).

``textfieldLabel`` should only be used for textfield questions, and it should be
a string that defines the textfield label (which is simply the text that is
inside the textbox before you type anything in and is at the top left of the
textbox once you start typing).

``handleMCQChange`` and ``handleResponseChange`` are functions from the parent
component that handles the collection of user responses for checkbox/radio
questions and free response questions.


Below, is an example of the component being used.
::

    <Question
        id={1}
        question="Name"
        choices={[]}
        questionType="text-field"
        textfieldLabel="Name"
        handleMCQChange={ handleMCQChange }
        handleResponseChange={ handleResponseChange }
    />


*************
Report
*************
The `Report component <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/frontend/src/components/report.js#L16>`_
generates a form where the users can submit their experiences to Discriminology.
The report component is called in the ``policing.js`` and ``suspension.js``
pages to generate forms on those pages.

The ``Report`` component takes a single ``category`` prop, which is the name of
the category as it is stored in the database. Using this category, the component
loads in all the questions for that category. Then, it calls on the
``CreateReport`` component to list the questions. Finally, it loads in the tags
that will be displayed at the bottom of the page.s

A new report page can be created as follows.

1. In a new javascript file, copy and paste the code in either ``policing.js``.

2. Rename the function `here <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/frontend/src/pages/policing.js#L6>`_
appropriately, and `here <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/frontend/src/pages/policing.js#L22>`_
as well.

3. In the ``Report`` component that is called `here <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/frontend/src/pages/policing.js#L17>`_,
change the string passed into the ``category`` prop to be the name of the
category that is stored in the questions table.

4. Add a route to the new page on ``frontend/src/App.js``. To do this import the
page `here <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/frontend/src/App.js#L3>`_
and add a new Route React element inside the Routes element.

*************
ReportHeader
*************

The `ReportHeader component <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/frontend/src/components/reportheader.js#L4>`_
generates a header used specifically at the top of all report pages. This
component combines the normal header component with the identical styling and
message that is used at the top of every report page. The ``header`` prop is the
name of the header.

*************
ReportsByCategoryChart
*************

The `ReportsByCategoryChart component <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/frontend/src/components/reportsbycategorychart.js#L8>`_
creates a doughnut chart that displays the number of reports divided by
category. This chart is displayed on the Top Level Insights page.

The ``ReportsByCategoryChart`` component visualizes reports that were filed
within a specified tiemframe. The times used to plot each report is the time the
user states that the incident occurred, not when the report itself was filed.
For example, if the user said that the incident happened in February 2022, but
files the report in November 2022, the incident will be plotted as occurring in
February.

If Discriminology adds a new category of report, it is very simple to update the
``ReportsByCategoryChart``. In the ``ReportsByCategoryChart``.js file, simply
add a new ``backgroundColor`` `here <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/frontend/src/components/reportsbycategorychart.js#L25>`_
to the ``dataConfig`` constant. This color will be the color of the category on
the doughnut chart.

The ``ReportsByCategoryChart`` generates a doughnut chart by accepting a ``data``
prop. ``data`` should be an array of objects, with each object in the array
representing one category of report. Every category of report should be
represented. Each object in the array should be structured as:
``{category: (category name), reports: (number of reports from given category)}``.

For example, the following is a sample ``ReportsByCategoryChart`` component.

::

    <ReportsByCategoryChart
        data={[{category: "Suspensions", reports: 44},
               {category: "Policing/Security", reports: 53}
             ]}
    />

*************
ReportsOverTimeChart
*************

The `ReportsOverTimeChart component <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/frontend/src/components/reportsovertimechart.js#L25>`_
creates a line graph that displays the number of reports for each category of
reports over time. This chart is displayed on the Top Level Insights page.

If Discriminology adds a new category of report, the following steps should be
taken to update the ``reportsovertimechart.js`` file.

1.  In the ``ReportsOverTimeChart`` component, add a new prop `here <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/frontend/src/components/reportsovertimechart.js#L25>`_,
named after the new category that the chart can accept. This new prop will be
used to pass data from the new category into the chart.

2. In the ``datasets`` section, located `here <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/frontend/src/components/reportsovertimechart.js#L49>`_
add a new object that follows the same pattern as the already existing
Suspensions and Policing/Security objects. The object fields has the following
properties. ``label`` controls what the new category is called on the chart.
``data`` references the new prop you defined in step 1. ``borderColor`` is the
color of the line on the line chart. ``backgroundColor`` is the secondary color
for the category on the chart. It is recommended that this color has the same
rgb values as the border color, except it's a value is 0.5. For example, if the
borderColor is ``rgba(6, 22, 140)``, the backgroundColor is recommended to be
``rgba(6, 22, 140, 0.5)``.

::

    <ReportsOverTimechart
        suspensions={[0, 0, 3, 1, 0, 2, 5, 0, 0, 0, 0, 1]}
        policingSecurity={[1, 0, 0, 0, 6, 3, 1, 0, 1, 0, 0, 0]}
        timeframe="month"
    />

*************
Tag
*************

The `Tag component <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/frontend/src/components/tag.js#L5>`_
creates one of the tags that is displayed at the bottom of the reports page. The
``Tag`` component takes in a ``label`` and a ``handleTagChange`` prop. The
``label`` is the name of the tag, passed in as a string. The ``handleTagChange``
is a function passed from the parent component to handle the change in state
for each tag (whether it has been clicked or not).

#############
Pages
#############

If the user is not logged in, the user will be redirected to the welcome page
when they try to access any of the internal pages. Once a user registers or
login, we use the ``localStorage`` to store the user's username. This is used to
associate a report with a user ID.

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
