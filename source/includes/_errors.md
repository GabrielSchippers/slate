# Errors

<aside class="notice">This error section is stored in a separate file in `includes/_errors.md`. Slate allows you to optionally separate out your docs into many files...just save them to the `includes` folder and add them to the top of your `index.md`'s frontmatter. Files are included in the order listed.</aside>

The Lift API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request isn't valid
401 | Unauthorized -- You must be authenticated to perform this action
403 | Forbidden -- You don't have the proper privileges to access this resource
404 | Not Found -- This resource wasn't found or you don't have priveleges to view it
409 | Conflict -- This resource already exists
422 | Validation Error -- There was a validation error
429 | Too Many Requests -- You're requesting too many kittens! Slow down!
500 | Internal Server Error -- The server failed to process your request
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
