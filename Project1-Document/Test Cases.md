#Test Cases Design

### Requirements

#### Server auth

- All servers share the same secret in the sysstem

- Only server sends the secret generated by the very first server can connect to the system successfully

#### Register
- Validate message
- Check if user exists locally
    - YES: send register failed msg and return false
    - NO:  check if username under register process( in the register list 
        - YES: send register failed msg and return false
        - NO: check if any remote servers exists
  				YES: broadcastToAll
  				NO: register succ

####  Login 

Login logic from Aaron

- Validate message

- if the user the gives no username on the command line arguments then login as anonymous on start

- if the user gives only a username but no secret then first register the user, by generating a new secret (print to screen for subsequent use), then login after/if receiving register success

- if the user gives a username and secret then login on start

- Login info in other servers: Design by ourselves: Enquiry with other servers if no user info exists locally
We need deal with it: https://app.lms.unimelb.edu.au/webapps/discussionboard/do/message?action=list_messages&course_id=_364937_1&nav=discussion_board_entry&conf_id=_729820_1&forum_id=_401176_1&message_id=_1697906_1

- Login failed message should be sent from server ad received by client if failed

#### Logout

- Send logout message to server

- Close connection immediately 


#### Client Load Broadcast

- every 5 seconds, every server broadcasts the loads of clients to the system 

#### Redirection

- Any one contains at least 2 clients less than itself, redirect client connection to that server

- After client received a redirection message, connect to given server automatically

#### Activity

- Clients send activities

- Servers do activities before broadcasting activities(exclude the one who sends) when recieved from other servers or clients

- Clients do activities when received activity message



 Testing of Functionality of  Server Auth
 Testing of Functionality of  Register
 Testing of Functionality of  Login
 Testing of Functionality of  Logout
 Testing of Functionality of  Load Announce
 Testing of Functionality of  Redirection
 Testing of Functionality of  Activity
