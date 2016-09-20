# Check all fields at once in Heroku connect object mapping

I did not see a way to check all the items in the object mapping and this can be frustrating often. The trick was to use jquery selector and set `checked` props to true.

- Open browser console by pressing F12.
- Insert the following code: `$('.hc-sfdc-field-list table tr > td:first-child input').prop('checked', true)`
- Click on Save and you should be good to go.
