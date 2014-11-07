1. undefined / null
2. Infinite / -Infinite
3. 3. isNaN
4. false, "", 0, NaN, null, undefined ===> false
5. 


2.2 Strings

x.length

"cat" + " say"

5 + " is my favourite number"

"hello john".indexOf(john) // run position, -1 means no result

"helloworld".substr(3,2) // start from 3, take 2 letters

"helloworld".slice(4,2) // start from 4, take 2 letters

"a,b,c,d".split(",") //['a',b'','c','d']

"abc dff      ".trim() // "abc dff"


--regular expression:
two ways: /[aA]{2,}/  or newRegExp("[aA]{2,}")

"aaoo".search(/[oO]{2,}/) //2
"aaoo".replace(/[aA]{2,}/, "b") // 'boo'



3. Use Objects
var o1 = new Object();
or var o2 ={}

var user={fisrtname:"marc", lastname:"cartle"}

user.sex="M" or user["sex"]="M"

var field ="animal"

user[field] ="cat"

delete user.sex  // return boolean

No user.length

Object.keys(user).length // return the number of keys

JSON
only difference
{"firstname":"marc", "lastname":"john"}

4. Arrays using numerical index
var arr1 = new Array();
or 
var arr2 = [];

arr2.length

typeof arr2 // return object

Array.isArray(arr2) // return boolean

var arr3 =['a', 'b', 'c']

arr3.lenght // return 3

for (var i =0;i<arr3.length;i++){console.log(arr3[i]);} // a, b, c

arr3[arr3.length]='bat'; // return bat

arr3.push('splat'); // return 5 (add one element at last position)

arr3[12]='fat'; // it is valid
arr3.length //return 13

arr3[10] // undefined

delete arr3[2] // the element is deleted, and assign an undefined value.
arr3.length // still return 13

// if you want to remove the element and all the elements after the removed element move forward one position

arr3.splice(2, 1) // start from 2, remove 1 element

arr3.push(100)

// return the number of elements, add 100 at the end

arr3.pop()

// return the last element and remove it in array.

arr.unshife(-10)

// add -10 to the first position

arr.shift()

// return the first element and remove it from array

a string to array

"1,2,3,4,5,6".split(',')

// return ['1', '2', '3', '4', '5','6' ]

an array to string

[1,2,3,4].join(":")

return '1:2:3:4'

sort array

var names=["marc", "Maria", "Alfred", "zimbu"];

names.sort()

// return [alfred, Maria, marc, zimbu]

names.sort(function(a,b) {
    var a1=a.toLowerCase(), var b1=b.toLowerCase();
    if(a1<b1) return -1;
    if(a1>b1) return 1;
    return 0;
});

// return [Alfred, marc, maria, zimbu]


names.forEach(function(value){console.log(value);});

//print out all names


5. make full use of functions


function hello(name) {console.log("Hello there " + name);}

hello("Marc")

// return Hello there Marc

hello()

// return Hello there

hello("Marc", true, 343543)

// still valid, and other than "Marc" parameters are ignored.

function hello2(){console.log(arguments);}

hello2("zhang", true, 233)

// return {'0':"zhang", "1":"true","2":233}


function init_cache(){}

//call init_cache(), 
//1.() -- use default values
//2.(number)--cache size only
//3.(object)-- we will use those instead

//anonymous function
var x = function(a, b){return a+b;}

x(2,3)
//return 5


function scope:

var pet="cat";
function show_pet(){var pet="dog"; console.log(pet);}

show_pet() // return dog

pet // return cat


6. Use language constructs
234 =='234' // true  == only compare value

234 ==='234' // false === identity operator compare both value and type

'' == false ==null==undefined==0 // true

''===false===0===null === undefined // false

var x = new Number(234)

x == 234 // true

x ===234 // false. x is an object

var user={fn:'marc',ln:'John', sex:'M'};
for (key in user) {
    console.log(key);
}

7. Inheritance and prototypes

'''javascript
function Shape(){
    this.X=0;
	this.Y=0;
	
	this.move=function(x,y){this.X=x; this.Y=y;}
	
	this.distance_from_origin=function(){ return Math.sqrt(this.X*this.X + this.Y*this.Y);}
}

var s = new Shape();
s.move(10,10);
console.log(s.distance_from_origin());
'''





