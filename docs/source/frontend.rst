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
To run the project, make sure npm is installed. Then, install all node modules
by running the following command.

::

    npm install


Then, to run the frotend, you can run

::

    npm run start


which will redirect you to the welcome page. This should be run in a different
terminal window from the backend. To view it in a mobile view, feel free to use
any mobile-viewing extension, like MobileView in VS Code.

#############
Components
#############

The following components serve as building blocks for the pages that we are
explained `here <https://discriminologydocs.readthedocs.io/en/latest/frontend.html#pages>`_.
They can be reused in new pages to keep the styling and functionality the same.
These will be located in the ``src/components`` folder.

*************
CreateReport
*************

The `CreateReport component <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/frontend/src/components/createreport.js#L6>`_
renders multiple questions at once so you do not need to call the ``Question``
component repeatedly to create a report page.

The ``CreateReport`` component accepts the following props: ``questions``,
``handleMCQChange``, and the ``handleResponseChange``. Using the information
passed through the ``questions`` prop, the ``CreateReport`` component displays
the ``Question`` component for each of the questions to generate a form. The
``questions`` prop is an array of objects that contains an ``id``, ``question``,
``options``, ``question_type``, and ``textfield_label``. See the ``Question``
component `here <https://discriminologydocs.readthedocs.io/en/latest/frontend.html#question>`_
for more information on these.

*************
Date
*************

The `Date component <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/frontend/src/components/date.js#L6>`_
renders a date question. The user can specify a date using a textbox or
selecting a date on a calendar pop-up.

The ``Date`` component accepts ``value`` and ``onChange`` props. The ``value``
defines the date displayed in the date component. ``value`` should be a
``dayjs`` object. ``onChange`` is the function passed down from the parent that
collects the user's response.

*************
Dropdown
*************

The `Dropdown component <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/frontend/src/components/dropdown.js#L6>`_
creates all the dropdown menus in the app. Given the name of a table, this
component loads all the entries in that table. For schools, this component will
display the city and state in addition to the school name. The options are
filtered to 10, but the options will continue to update as the user types.

The ``Dropdown`` component takes the following props: ``table``, ``name``,
``width``, and ``handleChange``. ``table`` is the name of the table to be
queried. ``name`` is the name that should be displayed as the default text.
``width`` defines the width of the dropdown menu. Finally, ``handleChange`` is
the function passed down from the parent component to handle changes to the
value of the dropdown.

Here is an example of the ``Dropdown`` component being called.
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

The `Error component <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/frontend/src/components/error.js#L3>`_
is used to display the error messages for invalid inputs. For example, it is
used in the registration page when the confirmation password does not match.
The only prop to the ``Error`` component is the ``message`` that you want to be
displayed as a string.

*************
Footer
*************

The `Footer componet <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/frontend/src/components/footer.js#L6>`_
displays the footer on the bottom of each of the internal pages. It currently
contains two buttons: one that takes the user to the homepage and another that
takes the user to a new report page.

*************
Header
*************

The `Header component <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/cb9c16a1dd16ed75bd18a8b0172156ea3e80c9c0/frontend/src/components/header.js#L3>`_
generates a header that is used at the top of all pages. The ``Header``
component accepts a ``header`` prop, which is the string that will be displayed
in the header.

*************
NewSchool
*************

The `NewSchool component <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/frontend/src/components/newschool.js#L12>`_
is a modal that allows users to add a new school. Once the button is clicked, a
modal will pop-up and allow users to enter the information for a new school.
Then, upon submitting, a nested modal will appear to confirm the submission.
From there, the user can return to the home page. An error will appear if any of
the fields (name, city, and state) are blank.

*************
Question
*************

The `Question component <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/frontend/src/components/question.js#L7>`_
renders a report question. The component can handle MCQ questions
(multiple-select and single-select questions) and textfield questions.

The question component accepts the following props: ``id``, ``question``,
``choices``, ``questionType``, ``textfieldLabel``, ``handleMCQChange``, and
``handleResponseChange``.

``id`` is the unique ID of the question as an integer.

``question`` specifies the question that is rendered. It should be a string that
defines the question's text itself (e.g. “Who are you?“).

``questionType`` defines what kind of question it is and should be defined as a
string amongst the following options: "checkbox", "radio", or "text-field". 
"checkbox" and "radio" are both multiple-choice style questions, but "checkbox"
allows for multiple choices to be selected, whereas "radio" only allows for one
choice to be selected. "text-field" is a free response text question.

``choices`` should only be included for multiple-choice questions and should be
an array of options like ``[“Yes”, “No”, “Maybe”]``.

``textfieldLabel`` should only be used for text-field questions, and it should
be a string that defines the textfield label (which is simply the text that is
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
ReportHeader
*************

The `ReportHeader component <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/frontend/src/components/reportheader.js#L4>`_
generates a header used specifically at the top of all report pages. This
component combines the normal header component with the identical styling and
an instructions message that is used at the top of every report page. The
``header`` prop is the name that will be displayed in the header.

*************
ReportsByCategoryChart
*************

The `ReportsByCategoryChart component <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/frontend/src/components/reportsbycategorychart.js#L8>`_
creates a doughnut chart that displays the number of reports per category.
This chart is displayed on the top level insight page.

The ``ReportsByCategoryChart`` component visualizes reports that were filed
within a specified tiemframe. The times used to plot each report is the time the
user states that the incident occurred, not when the report itself was filed.
For example, if the user said that the incident happened in February 2022, but
files the report in November 2022, the incident will be plotted as occurring in
February.

The ``ReportsByCategoryChart`` generates a doughnut chart by accepting a
``data`` prop. ``data`` should be an array of objects, with each object in the
array representing one category of report. Every category of report should be
represented. Objects in the array should be structured as:
``{category: (category name), reports: (number of reports from given category)}``.

For example, the following is a sample use of the ``ReportsByCategoryChart``
component.

::

    <ReportsByCategoryChart
        data={[
                {category: "Suspensions", reports: 44},
                {category: "Policing/Security", reports: 53}
             ]}
    />

*************
ReportsOverTimeChart
*************

The `ReportsOverTimeChart component <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/frontend/src/components/reportsovertimechart.js#L25>`_
creates a line graph that displays the number of reports for each category of
reports over time. This chart is displayed on the top level insights page.

The line chart will automatically update with new categories added via the
admin panel in the ``categories`` table. As mentioned in the database section,
``borderColor`` is the color of the line on the line chart. ``backgroundColor``
is the secondary color for the category on the chart. It is recommended that
this color has the same rgb values as the border color, except it's a value is
0.5. For example, if the ``borderColor`` is ``rgba(6, 22, 140)``, the
``backgroundColor`` is recommended to be ``rgba(6, 22, 140, 0.5)``.

The ``ReportsOverTimeChart`` generates a line chart by accepting a prop for
every category of report via the ``data`` prop and a ``timeframe`` prop. The
``data`` prop is a list of dictionaries for each category, where each dictionary
follows the following structure.

::

    {
        label: 'Suspensions',
        data: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12],
        borderColor: 'rgba(255, 99, 132)',
        backgroundColor: 'rgba(255, 99, 132, 0.5)'
    }


Here ``data`` is the array of numbers, where each number represents a datapoint
(the number of reports for the given category in a specified timeframe).  If the
"timeframe" prop equals ``month``, there should be 30 numbers in the array (one
for each of the past 30 days). If the ``timeframe`` prop equals ``month``, there
should be 12 numbers in the array (one for each of the past 12 months). The
numbers should be in chronological order within the array, with the earliest
datapoints coming first. The ``timeframe`` prop specifies whether the graph
represents data from the past month (past 30 days) or past year. This should be
a string that is either "year" or "month".

*************
Tag
*************

The
`Tag component <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/frontend/src/components/tag.js#L5>`_
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
associate a report with a user ID, upon submission.

*************
ChooseReport
*************

The `ChooseReport page <hhttps://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/frontend/src/pages/choosereport.js#L9>`_
lays out the options for categories of report that the user can fill out. The
page queries for all categories and prints a button for each category. Thus, no
changes need to be made to this page when a new category is added.

*************
ForgotPassword
*************

The `ForgotPassword page <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/frontend/src/pages/forgotpassword.js#L11>`_
allows users to reset their password through AWS Cognito. Users first enter
their email. Then, an email is sent to the address, if the user is an existing
user in the database. After that, a new window will appear with fields for a
reset code, a new password, and confirmation of the new password. If the code is
wrong or the email is not valid, an error will be displayed. The page also
checks that the confirmation password matches the given password.

*************
Homepage
*************

The `Homepage page <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/frontend/src/pages/homepage.js#L12>`_
is the landing page after the user logs in. It gives the user the option to
add a new report, view top level insights, or add a new school. The user can
also logout. This will clear all data stored in ``localStorage`` and redirect
the user back to the welcome page.

To view top level insights for a school, the user can select a school in the
dropdown menu and press "Search". The top level insights URL takes the school ID
as one of its parameters. Thus, the hompeage will redirect the user to the top
level insights page with the given school ID, when the form is submitted.

*************
Login
*************

The `Login page <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/frontend/src/pages/login.js#L11>`_
allows a user to log in through AWS cognito. If the username, email, and password
is not in the AWS Cognito User Pool, an error will be returned and displayed on
the page. The user is redirected to the homepage upon successful login.

*************
Registration
*************

The `Registration page <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/frontend/src/pages/registration.js#L13>`_
allows users to create a new account. The only required fields are the username,
email, and password. All other fields are optional. If no organization is
entered, the organization ID will default to 1, which is the ID for the default
organization.

When a user submits their registration request, a request is made to both the
AWS Cognito User Pool to add the new user and to the AWS RDS database. For
security reasons, the password is only stored in AWS Cognito. AWS Cognito
requires that the password be at least 8 characters in length and contain a
number, an uppercase, and a lowercase letter. If these requirements are not met,
an error will be displayed. Upon successful registration, the user is redirected
to the homepage. ``localStorage`` wil also be used to store the user's new
username.

*************
Report
*************
The `Report page <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/frontend/src/pages/report.js#L17>`_
generates a form where the users can submit their experiences to Discriminology.
The ``Report`` page takes the category ID as one of its parameters. Using this
category, the page loads in all the questions for that category. Then, it calls
on the ``CreateReport`` component to display the questions. Finally, it loads in
the tags that will be displayed at the bottom of the page.

*************
TopLevelInsights
*************

The `TopLevelInsights page <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/frontend/src/pages/toplevelinsights.js#L18>`_
displays two graphs for each school, given a school ID. The school ID is a
parameter passed through the URL. For example, the endpoint ``/insights/1`` will
return top level insights for the school with ID of 1, which is the default
school.

The first graph represents the distribution of reports among the different
categories for the given school through a pie chart. The second graph shows the
number of reports made for each category over a given timeframe through a line
chart. The user can choose whether the timeframe is the last month or the last
year.

*************
Welcome
*************

The `Welcome page <https://github.com/hcs-t4sg/hcs-t4sg-discriminology_project/blob/9eb3b105c94f68e8ddf96f987fff8aa0501d2083/frontend/src/pages/welcome.js#L5>`_
allows users to register, login, or continue as a guest. If the user chooses to
continue as a guest, the user's account will default to the default_user in the
``users`` table, with ID of 1. Then, the user can navigate to all pages per
usual.

#############
Other Files
#############
All environment variables are stored in the ``.env`` file. Here, we store the
API endpoint URL from the backend, so that when the server that hosts the
backend changes, all endpoints will automatically update.

The dependencies are all stored in ``package.json`` and ``package-lock.json``.

In the ``public`` directory, you will find the logo used for the site, as well
as the base ``index.html`` file.

In the ``src`` directory, you will also find all the styling used in the
``styles`` directory, divided by components and pages. The driver components is
located in ``App.js``, which contains the routes to all the pages that we have
defined. This component is initialized in the ``index.js`` file.
