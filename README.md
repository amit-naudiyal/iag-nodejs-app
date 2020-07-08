# iag-nodejs-app
iag-nodejs-app for Problem 2

# Instructions to run and test

+ Run application
	+ git clone https://github.com/Amit-Naudiyal/iag-nodejs-app.git
	+ cd iag-nodejs-app
	+ npm install
	+ node app.js

	+ Access on http://machine-ip:8080

+ Test Application (while your application is running...)
	+ cd iag-nodejs-app
	+ npm test

	+ expected output:
```
	  Status and content
    	Main page
      	  ✓ status
      	  ✓ content
    	About page
      	  ✓ status

  		3 passing (35ms)
```
+ Coverage (while your application is running...)
	+ cd iag-nodejs-app
	+ npm npm run coverage
	+ This shows the coverage report on console and also saves it under coverage/ folder as html.
