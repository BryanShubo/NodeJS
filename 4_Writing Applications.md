

###1. JSON server

```
var http = require('http');

function handle_incoming_request(req, res) {
    console.log("Incoming request:("+ req.method + ")" +req.url);
	
	load_album_list(function(err, albums) {
	    if(err != null) {
		    res.weriteHead(503, {
			"Content-Type": "application/json"});
			res.end(JSON.stringify({error:"file_error", message:err.message}) + "\n");
			return;
		}
		
		res.writeHead(200, {"Content-Type":"application/json"});
	    res.end(JSON.stringify({error:null, data:{albums: albums}})+"\n");
	})
	
}

function load_album_list(callback){
    fs.readdir('albums/', function(err, file_list) {
	    callback(err, file_list);
	}
}

var s = htt.createServer(handle_incoming_request);
s.listen(8080);

```


####2. Combine loops and asynchronous programming
stat is an asynchronous function

```
var http = require('http'),
    fs = require('fs');

function handle_incoming_request(req, res) {
    console.log("Incoming request:("+ req.method + ")" +req.url);
	
	load_album_list(function(err, albums) {
	    if(err != null) {
		    res.weriteHead(503, {
			"Content-Type": "application/json"});
			res.end(JSON.stringify({error:"file_error", message:err.message}) + "\n");
			return;
		}
		
		res.writeHead(200, {"Content-Type":"application/json"});
	    res.end(JSON.stringify({error:null, data:{albums: albums}})+"\n");
	})
	
}

function load_album_list(callback){
    fs.readdir('albums/', function(err, file_list) {
	    if (err) {
		    callback(err);
			return;
		}
		
		var dirs_only= [];
		
		(function iterator(i) {
		    if(i >= file_list.length) {
			    callback(null, dirs_only);
				return;
			}
		    fs.stat("albums/" + file_list[i], function(err, stats) {
			    if(err) {
				    callback(err);
					return;
				}
				
				if(stats.isDirectory()) {
				    dirs_only.push(file_list[i]);
				}
				iterator(i + 1);
			});
		})(0);
		
	}
}

var s = htt.createServer(handle_incoming_request);
s.listen(8080);
```

```
var arr;
var results;

(function iterator(i) {
    if(i >= arr.length) {
	    callback(null, results);
	} else {
	    async_work(function(err, res){
		    if(err){
			    callback(err);
			} else {
			    results.push(res);
				iterator(i + 1);
			}
		});
	
	}
})(0);
```

####3. Support multiple request types in your server

// /albums.json

// /albums/italy2012.json

```


```


