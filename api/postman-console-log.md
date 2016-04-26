# console.log in postman, chrome

If you are using Postman for API testing and want to see output of console.log, you have to enable debugging for packed apps and you should then be able to hit F12 and see the console.

Type the following in chrome address bar:

```
chrome://flags
```

Search for `packed` and you will see one saying `Debugging in packed apps` which you need to enable and you should be good to go.
