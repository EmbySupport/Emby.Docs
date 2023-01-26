Scheduled tasks are system operations that need to run periodically in order to keep your server up to date and running smoothly. Many of them take too long to be run within the normal library scan, so that's why we make them available as configurable scheduled tasks.

Scheduled tasks are accessed from the server dashboard by navigating to **Scheduled Tasks**.

You'll be presented with a list of scheduled tasks, for example:

![](images/server/scheduledtasks1.png)

Tasks can be run on demand anytime by clicking the play button on the right hand-side. Plugins can also install their own scheduled tasks to run periodically, and several of them do, e.g. Trakt.

Clicking on a task will display the triggers that cause the task to run:

![](images/server/scheduledtasks2.png)

The available triggers are:

* Daily at set time
* Weekly at set day and time
* Interval (Based on a number of hours)
* At application startup
* When the server resumes from sleep

Triggers can be removed by clicking the minus button on the right-hand side. Clicking the "Add Trigger" button will display a menu to add a trigger. The required fields will change depending on the trigger chosen.

![](images/server/scheduledtasks3.png)