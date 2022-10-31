# Regular Expressions in JavaScript

They are used to match patterns in strings. Syntax: `/regex/` (no quotations required.)

### Test Method

To test whether a regex matches a given string or not, call the `test` method on the regex, using the string as a parameter. It returns a Boolean value indicating whether the Regex is found in the given string.

```javascript
let mystr = "hello, world!";
let myRegex = /Hello/;
let result = myRegex.test(mystr); // false
```

### Match Method

To extract a match, call the `match` method on the given string, using the regex as a parameter. It returns an array object of matches.

```javascript
let mystr = "hello, world!";
let myRegex = /hello/;
let result = mystr.match(myRegex); // ["hello"]
```

#### Match Literal Strings

Literal strings are case sensitive

```javascript
let regex = /Hello/;
let string1 = "Hello", string2 = "hello";
let result1 = regex.test(string1); // true
let result2 = regex.test(string2); // false
```

#### Ignoring Cases

Use the `i` flag to ignore the cases. Case is placed after the end of regex.

```javascript
let regex = /Hello/i;
let string1 = "Hello", string2 = "hello";
let result1 = regex.test(string1); // true
let result2 = regex.test(string2); // true
```

#### Matching with Multiple Possibilities

Use the `|` (or) operator to check for multiple possibilities within the regex. The below example basically boils down to matching with 3 different regex, `/dog/`, `/cat/` and `/bird/`.

```javascript
let regex = /dog|cat|bird/;
```

#### Find Multiple Matches

Using the `g` flag it is possible to extract all the matching strings, instead of just the first match.

```javascript
let str = "Hello, hello, hello, is anybody in there?";
let regex = /hello/ig;
let result = str.match(regex); // ["Hello", "hello", "heLLo"]
```

#### Wildcard Character

`.` is a wildcard character. It can stand for anything.

```javascript
let str = "Look son, here comes the sun!";
let regex = /s.n/ig;
let result = str.match(regex); // ["son", "sun"]
```

#### Match a Single Character with Multiple Possibilities

Consider the example:

```javascript
let regex = /b[iuo]g/;
```

the first character is `b` the last character is `g` and the middle character can be any of these `i,u,o`. So the possible literal strings forming from this regex are: `big`, `bug` and `bog`.

```javascript
let vowelRegex = /[aeiou]/;
let str = "AabBcCdDeE";
let result = str.match(vowelRegex); // ["A", "a", "e", "E"]
```

#### Matching a Range

```javascript
let alphaRegex = /[a-z]/ig; // Matches all one character strings containing lowercase or uppercase alphabet.
```

```javascript
let myRegex = /[0-9]/ig; // Matches all one character strings containing a number.
```

``` javascript
let myRegex = /[2-6h-s]/ig; // Matches two ranges, 2-6, and h-s
```

- Shorthand character class `\w` matches `a-z`, `A-Z`, `0-9`, and `_`.

- Shorthand character class `\W` matches everything except alphanumeric characters. Its a negation of `\w`.
- Shorthand character class `\d` is used for matching digits from `0-9`.
- Shorthand `\D` is used for matching everything except digits.
- `\s` is used for whitespaces.

#### Negated Set

Will return everything that does **not** match the given regex. Use `^`operator.

```javascript
let myRegex = /[^0-9aeiou]/ig;
```

This will match everything except strings containing 0-9 or vowels.

#### Increasing Frequency of Regex Characters

- Use of `+` operator.  Implies occurrence one or more times.

```javascript
let difficultSpelling = "Mississipspi";
let myRegex = /s+/g; 
let result = difficultSpelling.match(myRegex); // ["ss", "ss", "s"]
```

- Use of `*` operator.  Implies occurrence zero or more times.

```javascript
let myRegex = /go*/g; // Returns strings like `g`, `go`, `goo`, `goooo`, and so on. 
```

```javascript
let myRegex = /[a-z]*/g // Returns any string containing lowercase alphabets.
```

- `a+ = aa*`

#### Greedy and Lazy matching

By default the longest matching string is returned(greedy). But you can have the smallest matching string too(lazy). Use `?` for lazy matching.

```javascript
let string = "titanic";
let regex = /t[a-z]*i/; 
string.match(regex); // ["titani"]
```

``` javascript
let string = "titanic";
let regex = /t[a-z]*?i/; 
string.match(regex); // ["ti"]
```

Another example

```javascript
let text = "<h1>Winter is coming</h1>";
let myRegex = /<.*>/; 
let result = text.match(myRegex); // ["<h1>Winter is coming</h1>"]
```

```javascript
let text = "<h1>Winter is coming</h1>";
let myRegex = /<.*?>/; 
let result = text.match(myRegex); // ["<h1>"]
```

#### Matching a Beginning String Pattern

`^` character (outside of the `[]`) can be used to match regex to only the **beginning** of the string.

```javascript
let calRegex = /^Cal/; // "Cal" should be at the beginning
let result = calRegex.test("Cal and Ricky"); // true
let result = calRegex.test("Ricky and Cal"); // false
```

#### Matching an Ending String Pattern

`$` is used for matching regex at ending of string.

```javascript
let lastRegex = /caboose$/; // "caboose" should be at end of the string
let result = lastRegex.test("I have caboose"); // true
let result = lastRegex.test("I caboose have"); // false
```

#### Quantity Specifiers

Set minimum and maximum length to be matched. Example, the string should be at least 2 characters long.

```javascript
let regex = /[A-Za-z]{2,}/
```

Syntax: `{min, max}`


# Test Yourself

#### Match Word or Phrase in a List  
#### Solution  
List-
- baloney
- darn
- drat
- fooey
- gosh darnit
- heck
(?i)(\W|^)(baloney|darn|drat|fooey|gosh\sdarnit|heck)(\W|$)
