# opencart-cron
Cron for Opencart 2.x

Crown implementation in Opencart 2.x to run controllers in the admin folder.

Tasks are registered in the admin / cron_tasks.php file as follows
``
$ cron-> call (
    "module / ocstore_badges / cron",
    array (
        "minute" => "*",
        "hour" => "*",
        "day" => "*",
        "dayofweek" => "*",
        "dayofmonth" => "*"
    ),
array (
"param1" => "value1",
"param2" => "value2",
...
"paramN" => "valueN"
)
);
``

The first parameter is the controller and the called method, in the example the cron () method is called in the admin / controller / module / ocstore_badges.php file
The second parameter is an array of parameters defining the start time. It can take the values ​​[\ d \\ - \ *, \ /].
Time values ​​are separated from each other by commas, for example "1,2,5".
Ranges of numbers can be specified with a dash, for example, "1-5", which is equivalent to "1,2,3,4,5".
To run the script every few minutes, you need to set the value "\ * / 10", which will be equivalent to the values ​​0, 10, 20, etc.
Use "*" to set any value.
The third parameter is an array of parameters passed to the method (optional).

For this script to work correctly, you need to add the following task to the task scheduler (cron, crontab) of the hosting panel:
``
Script (Command): /path_to_folder_with_your_site/admin/cron.php
Minute: *
Hour: *
Day of month: *
Month of year: *
Day of week: *
``

Examples:
1. Run the script every 5 minutes from 0 to 10 hours, on Sunday.
``
    array (
        "minute" => "* / 5",
        "hour" => "0-10",
        "day" => "*",
        "dayofweek" => "7",
        "dayofmonth" => "*"
    )
``
2. Running the script at midnight
``
    array (
        "minute" => "0",
        "hour" => "0",
        "day" => "*",
        "dayofweek" => "*",
        "dayofmonth" => "*"
    )
`` 
