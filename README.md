With this template, you can create virtual endpoints that simulates the behavior of the real service. Services on which your application depends on may be an unstable system that is not accessible all the time and that could potentially be a bottleneck in your testing process. With **Service Virtualization** you always have dependency available. This template is using open source tool **mountebank** which is most capable **Service Virtualization** tool in existence.

## To install the packages

Run the script ```npn install``` to install all the packages mentioned in package.json > dependencies

## Packages used
1) ejs - [Mountebank](http://www.mbtest.org/) supports EJS templates to upload the imposters (response stubs) through commandline.
2) Mountebank - To create virtual api endpoints with its responses. [Mountebank](http://www.mbtest.org/) has many features to predicate the API path, handle error scenarios, creating proxy and much more. 

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
