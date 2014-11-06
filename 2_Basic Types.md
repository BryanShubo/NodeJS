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

