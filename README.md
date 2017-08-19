
# Setting up Nightwatch and Selenium on Windows

## Install Java 8
The Java SDK is required to run Selenium.  Install a Java SDK from http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html

## Create a base folder
Create a folder named ```C:\dev```

## Install Node.js
- Under ```C:\dev``` create a New Folder named *nodejs*
- Go to http://nodejs.org and install *nodejs* in the new folder.
- The *npm* tool that is installed with *nodejs* is very old; update it using: ```npm install npm -g```

## Install nightwatch.js
- Under ```C:\dev``` create a New Folder named *nightwatch*
- Open a *nodejs* console window and change to the ```C:\dev\nightwatch``` directory
- Type ```npm install nightwatch```

## Install Selenium Server
- Download the Selenium jar file Version 3.5 from http://selenium.release.storage.googleapis.com/index.html
- Place the file in the ```C:\dev\nightwatch\lib\``` folder
- Rename the file to ```sel-serv.jar``` to make it easier to reference

## Install the Chrome Driver for Selenium
- Download the Chrome Driver from http://chromedriver.storage.googleapis.com/index.html
- Extract the executable into the directory ```C:\dev\nightwatch\lib\```
- Configure nightwatch to use the Chrome driver by modifying the file ```C:\dev\nightwatch\node_modules\nightwatch\bin\nightwatch.json```:

	  "selenium" : {
        "start_process" : false,
        "server_path" : "",
        "log_path" : "",
        "host" : "127.0.0.1",
        "port" : 4444,
        "cli_args" : {
          "webdriver.chrome.driver" : "C:/dev/nightwatch/lib/chromedriver.exe",
          "webdriver.ie.driver" : "",
          "webdriver.firefox.profile" : ""
        }
      },

## File to call the runner
- Create a new file: ```C:\dev\nightwatch\node_modules\nightwatch\nightwatch.js```
- Add this line and save the file:  ```require('nightwatch/bin/runner.js');```


# Running Tests

## Start Selenium
- Open a console window and navigate to ```C:\dev\nightwatch\lib```
- Use java to start Selenium: ```java -jar sel-serv.jar```
- Open Chrome and navigate to http://localhost:4444/wd/hub

## Run Tests
- Open a ```node.js``` console
- Navigate to ```C:\dev\nightwatch\node_modules\nightwatch```
- Run all tests: ```node nightwatch.js```
- Run a group of tests: ```node nightwatch.js -g google```
- Run a single test: ```node nightwatch.js -t examples/tests/nightwatch.js```
