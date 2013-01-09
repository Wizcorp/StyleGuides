##Naming Conventions

- When constructing string IDs or ID prefixes in the code, do not use "dojo", "dijit" or "dojox" in the names. Because we now allow multiple versions of dojo in a page, it is important you use _scopeName instead (dojo._scopeName, dijit._scopeName, dojox._scopeName).

- Names representing modules SHOULD be in all lower case.

- Names representing types (classes) MUST be nouns and written using CamelCase capitalization:
```javascript
	Account, EventHandler
```
- Constants SHOULD be placed within a single object created as a holder for constants, emulating an Enum; the enum SHOULD be named appropriately, and members SHOULD be named using either CamelCase or UPPER_CASE capitalization:
```javascript
	var NodeTypes = {
		Element : 1,
		DOCUMENT: 2
	}
````
- Abbreviations and acronyms SHOULD NOT be UPPERCASE when used as a name:
```javascript
	getInnerHtml(), getXml(), XmlDocument
```
- Names representing methods SHOULD be verbs or verb phrases:
```javascript
	obj.getSomeValue()
```
- Public class variables MUST be written using mixedCase capitalization.

- CSS variable names SHOULD follow the same conventions as public class variables.

- Private class variables MAY be written using _mixedCase (with preceding underscore):
```javascript
	var MyClass = function () {
		var _buffer;
		this.doSomething = function () {
		};
	}
```
- Variables that are intended to be private, but are not closure bound, SHOULD be prepended with a "_" (underscore) char:
```javascript
	this._somePrivateVariable = statement;
```
> Note: the above variable also follows the convention for a private variable.

- Generic variables SHOULD have the same name as their type:
```javascript
	setTopic(topic) // where topic is of type Topic
```
- All names SHOULD be written in English, American English.

- Variables with a large scope SHOULD have globally unambiguous names; ambiguity MAY be distinguished by module membership. Variables with small or private scope MAY have terse names.

- The name of the return object is implicit, and SHOULD be avoided in a method name:
```javascript
	getHandler(); // NOT getEventHandler()
```
- Public names SHOULD be as clear as necessary and SHOULD avoid unclear shortenings and contractions:
```javascript
	MouseEventHandler // NOT MseEvtHdlr
```
Note that, again, any context that can be determined by module membership SHOULD be used when determining if a variable name is clear. For example, a class that represents a mouse event handler:
```javascript
	dojo.events.mouse.Handler // NOT dojo.events.mouse.MouseEventHandler
```
- Classes/constructors MAY be named based on their inheritance pattern, with the base class to the right of the name:
```
EventHandler
UIEventHandler
MouseEventHandler
```
The base class CAN be dropped from a name if it is obviously implicit in the name:
```javascript
	MouseEventHandler // as opposed to MouseUIEventHandler
```


##Specific Naming Conventions


- The terms get/set SHOULD NOT used where a field is accessed, unless the variable being accessed is lexically private.

- The "is" prefix SHOULD be used for boolean variables and methods. Alternatives include "has", "can" and "should"

- The term "compute" CAN be used in methods where something is computed.

- The term "find" CAN be used in methods where something is looked up.

- The terms "initialize" or "init" CAN be used where an object or a concept is established.

- UI Control variables SHOULD be suffixed by the control type. Examples: leftComboBox, topScrollPane

- Plural form MUST be used to name collections.

- A "num" prefix or "count" postfix SHOULD be used for variables representing a number of objects.

- Iterator variables SHOULD be called "i", "j", "k", etc.

- Complement names MUST be used for complement entities. Examples: get/set, add/remove, create/destroy, start/stop, insert/delete, begin/end, etc.

- Abbreviations in names SHOULD be avoided.

- Negated boolean variable names MUST be avoided:
```javascript
	isNotError, isNotFound are unacceptable.
```

- Exception classes SHOULD be suffixed with "Exception" or "Error" .. FIXME (trt) not sure about this?

- Methods returning an object MAY be named after what they return, and methods returning void after what they do.


##Files

- Class or object-per-file guidelines are not yet determined.

- Tabs (set to 4 spaces) SHOULD be used for indentation.

- If your editor supports "file tags", please append the appropriate tag at the end of the file to enable others to effortlessly obey the correct indentation guidelines for that file:
```javascript
	// vim:ts=4:noet:tw=0:
```

- The incompleteness of a split line MUST be made obvious :
```javascript
	var someExpression = Expression1
		+ Expression2
		+ Expression3;
	var o = someObject.get(
		Expression1,
		Expression2,
		Expression3
	);
```
Note the indentation for expression continuation is indented relative to the variable name, while indentation for parameters is relative to the method being called.
Note also the position of the parenthesis in the method call; positioning SHOULD be similar to the use of block notation.


##Variables

- Variables SHOULD be initialized where they are declared and they SHOULD be declared in the smallest scope possible. A null initialization is acceptable.
- Variables MUST never have a dual meaning.
- Related variables of the same type CAN be declared in a common statement; unrelated variables SHOULD NOT be declared in the same statement.
- Variables SHOULD be kept alive for as short a time as possible.
- Loops / iterative declarations
	- Only loop control statements MUST be included in the "for" loop construction.
	- Loop variables SHOULD be initialized immediately before the loop; loop variables in a "for" statement MAY be initialized in the "for" loop construction.
	- The use of "do...while" loops is acceptable (unlike in Java).
	- The use of "break" and "continue" is not discouraged (unlike in Java).

- Conditionals
	- Complex conditional expressions SHOULD be avoided; use temporary boolean variables instead.
	- The nominal case SHOULD be put in the "if" part and the exception in the "else" part of an "if" statement.
	- Executable statements in conditionals MUST be avoided.

- Miscellaneous
	- The use of magic numbers in the code SHOULD be avoided; they SHOULD be declared using named "constants" instead.
	- Floating point constants SHOULD ALWAYS be written with decimal point and at least one decimal.
	- Floating point constants SHOULD ALWAYS be written with a digit before the decimal point.


##Layout


### Block statements.

* Block layout SHOULD BE as illustrated below:
```javascript
	while (!isDone) {
		doSomething();
		isDone = moreToDo();
	}
```

* if statements SHOULD have the following form:
```javascript
	if (someCondition) {
		statements;
	} else if (someOtherCondition) {
		statements;
	} else {
		statements;
	}
```

* for statements SHOULD have the following form:
```javascript
	for (initialization; condition; update) {
		statements;
	}
```

* while statements SHOULD have the following form:
```javascript
	while (!isDone) {
		doSomething();
		isDone = moreToDo();
	}
```

* do...while statements SHOULD have the following form:
```javascript
	do {
		statements;
	} while (condition);
```

* switch statements SHOULD have the following form:
```javascript
	switch (condition) {
	case ABC:
		statements;
		//  fallthrough
	case DEF:
		statements;
		break;
	default:
		statements;
		break;
		// need a break keyword on the last case
	}
```

* try...catch...finally statements SHOULD have the following form:
```javascript
	try {
		statements;
	} catch (ex) {
		statements;
	} finally {
		statements;
	}
```

* A single statement if-else, while or for MUST NOT be written without brackets, but CAN be written on the same line:
```javascript
	if (condition) { statement; }
	while (condition) { statement; }
	for (intialization; condition; update) { statement; }
```

### Whitespace

* Conventional operators MAY be surrounded by a space (including ternary operators).

* The following reserved words SHOULD NOT be followed by a space:

	- break
	- catch
	- continue
	- do
	- else
	- finally
	- for
	- function if anonymous, ex. var foo = function (){};
	- if
	- return
	- switch
	- this
	- try
	- void
	- while
	- with

* The following reserved words SHOULD be followed by a space:

	- case
	- default
	- delete
	- function if named, ex. function foo() {};
	- in
	- instanceof
	- new
	- throw
	- typeof
	- var

* Commas SHOULD be followed by a space.

* Colons MAY be surrounded by a space.

* Semi-colons in for statements SHOULD be followed by a space.

* Semi-colons SHOULD NOT be preceded by a space.

* Function calls and method calls SHOULD NOT be followed by a space. Example: doSomething(someParameter); // NOT doSomething (someParameter)

* Logical units within a block SHOULD be separated by one blank line.

* Statements MAY be aligned wherever this enhances readability.

### Comments

* Tricky code SHOULD not be commented, but rewritten.

* All comments SHOULD be written in English.

* Comments SHOULD be indented relative to their position in the code, preceding or to the right of the code in question.

* The declaration of collection variables SHOULD be followed by a comment stating the common type of the elements in the collection.

* Comments SHOULD be included to explain BLOCKS of code, to explain the point of the following block.

* Comments SHOULD NOT be included for every single line of code.


