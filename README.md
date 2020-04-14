# Template for Mountebank setup

## To install the packages

Run the script ```npn install``` to nstall all the packages mentioned in package.json > dependencies

## Packages used
1) ejs - Mountebank supports EJS templates to upload the imposters (response stubs) through commandline.
2) Mountebank - To handle mountebank events

## Scripts to run mountebank
npm run mock , In package.json ``"mock": "mb --configfile mountebank/imposters.ejs --loglevel debug"``

The above scripts 3 important parts,
1) ```mb``` -> to start the mountebank in default host and port ```http://localhost:2525```
2) ```--configfile mountebank/imposters.ejs``` -> This command line flag is suggesting to load the imposters available in imposters.ejs. By this mountebank will make PUT call to ```localhost:2525/imposters``` to push all the stubs. After this all the API's will be exposed to ```<Protocol>://localhost:<Port>/<Path>``` mentioned in imposters.
3) ``` --loglevel debug``` -> This would show the log in the terminal where ```npm run mock``` was started. Apart from ```mb.log``` will be created in the project having the logs.

## Types of response created
1) JSON
2) XML

## How to test API

API tools like Postman, SOAPUI etc. can be used to test the API's by giving appropriate method, port and protocol mentioned in imposters.
