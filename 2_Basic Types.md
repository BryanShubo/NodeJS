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

4. Arrays
5. numerical index
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
















