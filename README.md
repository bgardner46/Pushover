Pushover Notification Service

The pushover plug-in provides notification service by communicating with the Pushover Service (https://pushover.net).

API and User keys must be obtained from Pushover and entered in the Configuration Screen.

Notifications can be sent via a serial command or by other plugins.

Serial Command
    serial_prefix {options} messageserial_postfix
"Serial prefix string" and "Serial terminator characters" should be set in the Configuration Screen.
Serial command options and message adhere to the same format as that used by the procedure call from other plug-ins. See below.

Examples: (assumes "Serial prefix string" is "pushover:", "Serial terminator characters" is ";")

Send a message with default parameters (typical use).

    pushover: Hello World!;

Send a message to specific devices and log:
    pushover: -l -d bobsphone,wphone Hello World;
pushover Procedure
Other plug-ins can send notifications using the pushover procedure.
   pushover { -t title | -p priority | -d device1,device2 | -s sound | -ttl seconds | -l } message
-t title

Title for message. If title is more than one word, enclose in double quotes or braces.


-p priority

Priority of message. A value of -2, -1, 0 (default), 1, or 2{,r{,e}}.
For priority 2, r = retry time (default: 60, min: 30), e = expire time (default: 1800, max: 10800)


-d device(s)

List of devices to send to, comma separated if more than one. Default: all devices.


-s sound

Notification sound. Default: "echo".


-ttl seconds

Time to live, after which the message will be deleted. Default: Device behavior for notifications.


-l

Log this command to Pushover log.


message

Message to send. Must come after all options. Does not need to be enclosed in quotes.

Invalid options, along with any other options that follow, will be interpreted as part of the message.

Examples:

Send a message with default parameters (typical use).
    pushover Hello World! 

Send a message to specific devices and log:
    pushover -l -d bobsphone,wphone Hello World

Send a message with emergency priority every 30 secs for 15 mins and log:
    pushover -l -p 2,30,900 Water Leak Detected in Utility Room!

Send a message with emergency priority every 45 secs for 30 mins and log:
    pushover -l -p 2,45 Water Leak Detected in Utility Room!# Pushover

