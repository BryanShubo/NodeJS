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
```


###3.3 Solving a new problem that arises in Node.js-losing your "this" pointer

```
var fs = require('fs');

function FileObject(){
    this.filename = null;
	
	this.exists = function(callback) {
	console.log("attempting to verify: " + this.filename);
	fs.open(this.filename,'r', function(err,handle){
	    if(err) {
		    console.log(this.filename + " does NOT exist");
			callback(false);
		} else {
		    console.log(this.filename + ' does INDEED exist');
			callback(true);
			fs.close(handle);
		}
	});
	};
}

var fo = new FileObject();
fo.filename = 'a;dja;d';

fo.exists(function(does_it_exist){
    console.log("results from exist: " + does_it_exist);
});
```

// return: attempting to verify: a:dja:d
undefined does NOT exist
results from exist:false

in fs.open function, "this" reference does not point to object FileObject any more, so this.filename is fs.open function is null.

Solution:

```
var fs = require('fs');

function FileObject(){
    this.filename = null;
	
	this.exists = function(callback) {
	var self = this;
	console.log("attempting to verify: " + this.filename);
	fs.open(self.filename,'r', function(err,handle){
	    if(err) {
		    console.log(self.filename + " does NOT exist");
			callback(false);
		} else {
		    console.log(self.filename + ' does INDEED exist');
			callback(true);
			fs.close(handle);
		}
	});
	};
}

var fo = new FileObject();
fo.filename = 'a;dja;d';

fo.exists(function(does_it_exist){
    console.log("results from exist: " + does_it_exist);
});
```


###3.4 Yield control and improve responsiveness

Yield control to tell node to execute the next function.

####1) process.nexttick(callback);
####2) setImmediate(callback);






