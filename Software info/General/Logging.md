With the logging module imported, you can use something called a “logger” to log messages that you want to see. By default, there are 5 standard levels indicating the severity of events. Each has a corresponding method that can be used to log events at that level of severity. The defined levels, in order of increasing severity, are the following:

-   DEBUG
-   INFO
-   WARNING
-   ERROR
-   CRITICAL
By default, the logging module logs the messages with a severity level of `WARNING` or above

## Basic configuration
````
import logging

logging.basicConfig(filename='app.log', filemode='w', level=logging.DEBUG, format='%(name)s - %(levelname)s - %(message)s')
logging.warning('This will get logged to a file')
````

The messages will be logged in a filename <app.log>  
The root logger will be set to the specified severity level. 


## Handlers
Handlers come into the picture when you want to configure your own loggers and send the logs to multiple places when they are generated. Handlers send the log messages to configured destinations like the standard output stream or a file or over HTTP or to your email via SMTP.
