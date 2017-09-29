## Sonis Return Messages

**Sonis.cfc**, *ocu/cfc/sonis.cfc*, is alive! Today you can find a fancy new method of passing data and messages around.

Inside the component you will find **returnMessage()** and **returnEnd()**. Use of these allow us to generate clean, consistent code. Detailed success and error messages are now sent back to the user along with the data.

When invoked, a structure housing all data and messages is returned in one package. **Each developer can tap into any function in the system and knows what to expect in return.** 

>No more rebuilding. No more duplicating. No more debugging. Clean and consistent payloads.

----------


ReturnMessage()
-------------
```javascript
returnMessage(success, status, message, returnData, log, logMessage, logType);
```
  - **success** - *boolean* required (*true*|*false*)
 - **status** - *string* required (For decision functions or display to user)
 - **message** - *string* required (Message details of operation, for user display)
 - **returnData** - *string* default = blank (Holds query results, exception data, file data, or left blank etc.) 
 - **log** - *boolean* default = false (If true, creates log entry on application.log)
 - **logMessage** -*string* optional (Message to be written to log, usually inside catch)
 - **logType** - *string* default = information (Specifies log entry category: *information* | *warning* | *error* | *fatal*)
 - ---
 

**Success:**  Anything can be placed in returnData, such as the results from another function call.

```javascript
return returnMessage(success=true, status='Success', message='File has been moved.', returnData = fileResult);
```
![Success Response](http://johnbocook.com/hosted/sonis/returnMessageTrue.png)

---


**General Error:** Placed inside a catch, the failed action is returned to the calling page with an error message that can be shown on the users screen or via console.log for to debug javascript. Here the message is being appended with the the exception output *(& e.message)* to give even more detail. 
```javascript
return returnMessage(success=false, status='Error', message='An error has occured. ' & e.message);
```
<br>

![General Error Response](http://johnbocook.com/hosted/sonis/returnMessageGenError.png)



**Specific Error:** When  called from a catch, specific returnMessages can be called based on the type of exception thrown. 

```javascript
return returnMessage(success=false, status='Error', message='Invalid MimeType', returnData=e.Mimetype, log = true, logMessage = 'Invalid Mimetype: '& e.Mimetype, logType = 'error');
```
<br>

> **Note:**
> - *Log*, *LogMessage* and *LogType* are all optional. They were omitted in the General Error example above. Sometimes, you don't need to log the error, especially on cases where a non-existent file failed to be deleted.
> - *Data* will always be populated. It always defaults to blank, unless you passing data into the argument. 

