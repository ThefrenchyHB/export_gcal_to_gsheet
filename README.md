# export_gcal_to_gsheet
The export_gcal_to_gsheet function is designed to export events from a Google Calendar to a Google Sheet within a specified date range. Let's break down what this function does and how it accomplishes the task:

Authentication and Calendar Retrieval:

It first retrieves the email address of the current user (Session.getActiveUser().getEmail()) to identify the Google Calendar associated with that user.
Then, it fetches the calendar using the ID obtained.
Date Range Determination:

The function retrieves the start and end dates for the event export from cells B3 and D3 of the active sheet, respectively.
It increments the end date by one day to ensure that events occurring on that day are excluded.
Clearing Previous Data:

It clears the contents of rows after row 6 in the Google Sheet to remove any previous event data. This ensures that only the latest events are displayed.
Event Retrieval:

Using the determined start and end dates, it retrieves events from the Google Calendar within the specified date range.
Optionally, it filters the events to include only those that match a specific search query, specified here as '-project123'.
Formatting and Population:

It formats the retrieved events into a structured format suitable for display in the Google Sheet.
It sets the header row in the Google Sheet with labels for different event attributes.
It populates the Google Sheet with event details, placing each event's attributes (such as start time, end time, title, location, and description) in separate columns.
Batch Write Optimization:

To optimize performance, it uses batch writes to set event details in the Google Sheet. This approach minimizes the number of interactions with the Google Sheets API, improving efficiency, especially for larger datasets.
Weekday Retrieval:

It includes a helper function getWeekDay that converts a date object into the corresponding weekday name (e.g., Sunday, Monday, etc.). This function is used to determine the weekday of each event's start date.
Overall, this function automates the process of exporting recent events from a Google Calendar to a Google Sheet, providing a convenient way to review and analyze event data.
