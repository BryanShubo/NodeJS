##3.1 Compare synchronous and asynchronous programming



###3.1 Compare synchronous and asynchronous programming

```
<?php

$f=fopen('test.txt', 'r');
$contents = fread($f,100000);
echo $contents;
fclose($f);
>
```

```
var fs = require('fs');

fs.open('test.txt','r' function(err,handle){
    var f = handle;
	var b = new Buffer(100000);

    fs.read(f,b,0,100000,null,function(err,bytes_read){
        console.log(b.toString("utf8", 0,bytes_read));
	    fs.close(f);
    });
});

```


###3.2 Mix error handling and asynchrounous programming

Standard try catch block

```
try{
	throw new Error("DANGER ZONE!");
} catch(e) {
    console.log("I caught the error PHEW!");
}
```

The following way will return error
```
try{
    setTimeout(function(){
	    throw new Error("DANGER ZONE!");
	}, 2000);
    
} catch(e) {
    console.log("I caught the error PHEW!");
}
```

Correction way:
```

setTimeout(function(){
    try{ throw new Error("DANGER ZONE!")
	} catch(e) {
    console.log("I caught the error PHEW!");
    }
	}, 2000);
```


```
var fs = require('fs');

fs.open('test.txt','r' function(err,handle){

    fi (err == null) {
    var f = handle;
	var b = new Buffer(100000);

    fs.read(f,b,0,100000,null,function(err,bytes_read){
        if (err == null) {
		console.log(b.toString("utf8", 0,bytes_read));
	    fs.close(f);
		} else {
		    console.log("Oh, No ! fail on open: " + err.code + " " + err.message);
		}
    });
	} else {
	    console.log("Oh, No ! fail on open: " + err.code + " " + err.message);
	}
});



###3.3 Solving a new problem that arises in Node.js-losing your "this" pointer
```








