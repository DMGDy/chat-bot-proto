# Things To get Done

## Create Webpage for user to interact with and Client side Logic with Javascript
0. Create input element for user to enter WIN#
1. Create Box for user to enter text (their question)
2. Create element to update chat window on asked questions/received
answers
3. Update Chat window element with AI Response
    * Depending on AI API, update whenever a word is received rather than 
    waiting for entire response
4. Send POST with WIN# to server and obtain symmetric session key
5. HTTP Method POST on WIN# once input element even receives enter
    * Do not create chat window element or input element for prompt
    until response is received from server
6. Create HTTP Method POST of user prompt once available tokens is determined to be sufficient
    * Calculation should probably be done on the server since total tokens
    is likely available to do with AI API
5. HTTP GET method request for any available parts of response available
(or entire response)

## Create REST API Backend Server Logic
0. Receive and generate JWT (JSON Web Token) for symmetric session key
and give to client along side number of tokens available for user
    1. Have a form of database (preferably CSV/XML) for WIN# and 
    available tokens for each
1. Receive prompt from user and respond notifying it has been received
2. Response to GET request with any portion of response, or entire 
response (API dependent)
    1. If an extrenuous prompt was received from user, discard
    and notify that this cannot respond to such requests/texts

## AI API Handling 
0. Provide Context window for AI
    * FAQ Document
    * Official SPURs documentation
    * Any other related document to help answer questions
1. Request total keys available
    * Math to be done on how it can be divided equally per student
2. Make request to AI API (preferably REST API or native library) with
user question
3. provide each portion of AI response to Server logic portion
4. Save question and response for the session and provide to
context window for more accurate responses

## Configure Serverside 
0. Configure nginx to host server with necessary files
    * html, javascript, css, any images used as assets
1. Listen on for both IPv4 and IPv6 (dual-stack server)
2. Provide redirection to error page
3. Create systemd service for nginx (if not created already) and log
connections to a file
4. Create systemd service for web server program
    * Requires nginx to be up
    * restart if crashes
    * Log to file from stdout and stderr
