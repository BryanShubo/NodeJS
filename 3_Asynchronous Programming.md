##3.1 Compare synchronous and asynchronous programming



###3.1 Compare synchronous and asynchronous programming

···
<?php

$f=fopen('test.txt', 'r');
$contents = fread($f,100000);
echo $contents;
fclose($f);
>
···
