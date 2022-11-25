# Planning test cases for the login screen

## The goal is to cover critical scenarios, as well as a few minor scenarios.
## Not many edge cases will be covered.
### I'll be organizing my test cases as follows: 

Example: 
- Assert that a feature does what is expected. More context: [context], images may be utilized/linked to make it easier to understand.


Onto the test.

## Web cases for basic login: 

1. Assert that upon providing a valid email, the user can log in successfully upon clicking the continue + log in button. **This is a critical test** .
1. Assert that the user cannot click "continue" without providing a valid email address.  **This is a critical test**.
2. Assert that the user cannot click "continue" without providing a valid mobile number. **This is a critical test**.
2. Assert that an email address is valid. Valid emails are in the format ```xxxx@emailprovider.domain```.
4. Assert that a phone number is valid for the given country. For example, if I choose Brazil as my country, phone formats should be ```(99)99999-9999```. 
4. Changing the website's language should change the language of the "Support" widget. Context: ![Alt](/supportLanguage.png "Image explaining the undesired behavior.")
5. Trying to log in with an unregistered email address should return an "invalid email" message.
6. Trying to log in with an unregistered phone number should return an "invalid email" message.
7. Uploading the same file multiple times should not be allowed on the support widget. 
* Desired behavior: print out a warning message to the user reminding them that a similar file is already in place. Context: ![Alt](/multipleFiles.png "Image explaining the undesired behavior.")

## Mobile cases for basic login: 

For the sake of time and saving characters, mobile tests should be almost identical to the web tests, but assuring that the website is responsive to different screen sizes and ratios. 



## Web cases for the "I have a code" part:

These are done assuming a valid ``` xxxx-xxxx-xxxx-xxxx ``` code.

1. First name AND Last name fields should accomodate for special characters such as ```ç, ß, æ ``` and more. **This is a critical test**.
2. Password field **must** comply to the rules provided. Assert that the rules on the image are followed such as the ```aA3bsz1@``` password is valid but the ```a``` isn't. 
  * Context: ![Alt](/password.png "Password field ruleset")
4. Name fields should NOT be able to receive numbers as a valid response. Expected behavior: print a warning reminding the user that name fields should be characters only. 
  * Context: ![Alt](/numbersnames.png "Numbers on name fields should not be allowed.") **This is a critical test**
6. Name fields should NOT be able to receive query statements OR should be ignored on the back-end of the application. 
  * Context: ![Alt](/sql.png "SQL query on name fields")
8. If the code provided isn't valid, it should print an error to the user to let them know their code is not valid OR they miscopied it. **This is a critical test**
9. Upon clicking Activate, if everything else is valid, the user account should be activated. **This is a critical test**.


## Mobile cases for the "I have a code" part:

For the sake of time and saving characters, mobile tests should be almost identical to the web tests, but assuring that the website is responsive to different screen sizes and ratios. 





# How would you organize the test cases if there were hundreds of them?

I believe using Jira or any other project tracking software would be ideal for this. In my case and example, I created an "Epic", a feature proposition/idea that should be broken down into smaller tasks(stories).

I'm not sure how to invite the Voxy team to the Jira project, so I'll just link a few images that should, hopefully, clarify how I'd envision Jira to be used. Tasks would be given an importance level (High, medium, low, backlog) and should be prioritized as such.

![Alt](/Jira.png "Example of a Jira structure")

The epic would be the main feature to be tested/have test cases built, the subtasks or items would be the actual test cases for a given feature. I'm sure there are better ways to do it, but I'm not familiar with them.



# Suggestions (?)

The login API doesn't seem to have a limitation (or I didn't try hard enough) against multiple failed requests from the same origin. It seems that I could, for example, spam the authorization endpoint ``` https://app.voxy.com/api/v0/authentication/organization/user/USEREMAIL@EMAIL.COM ``` without any issues, instead of having my requests blocked.

