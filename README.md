# Style Guide

## What exactly is a style guide?

Before we begin, let us remind ourselves exactly what a code style guide is:

A style guide or style manual is a set of standards for the writing and design of code. The implementation of a style guide provides uniformity in code style and formatting, often covering guidelines regarding indentation (tabs vs. spaces), variable and function naming conventions, where best to apply whitespace and so on.


## Why is consistent code style important?

They say that good code is it's own documentation. We don't completely agree with this (docs are important!), the fact is, the more readable our source code is, the easier it is to maintain.

Following a consistent style guide both helps enforce this concept and improves the overall quality of the code we write. This facilitates other developers stepping in to assist with maintenance more easily and can certainly save time in the long haul.

Readable source code is arguably easier to understand as well. It's easier to browse, locate and fix bugs in and more easy to optimize. It can also give us a clearer picture of how the code fits into a larger body of work.

Consistently styled code can:
- Reduce the lead time required to understand an implementation
- Make it easier to establish what code can be reused
- Clarify how updates to an implementation should be styled or structured (remember that consistent code, even when written by a team, should look like one person wrote it).

##Naming Conventions

- Names representing modules SHOULD be in all lower case.

- Names representing types (classes) MUST be nouns and written using CamelCase capitalization:
```javascript
	Account, EventHandler
```
- Constants SHOULD be named using UPPER_CASE capitalization and if multiple, SHOULD be placed within a single object created as a holder for constants, emulating an Enum; the enum SHOULD be named appropriately:
```javascript
	var MAX_LEVEL = 5;
	var playerAttribute = {
		EARTH : 1,
		WATER: 2,
		FIRE: 3
	};
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

- Methods returning an object MAY be named after what they return, and methods returning void after what they do.


##Files

- Class or object-per-file guidelines are not yet determined.

- Indentation MUST use real tabs.


- The incompleteness of a split line MUST be made obvious :
```javascript
	var o = someObject.get(
		Expression1,
		Expression2,
		Expression3
	);
```


##Variables

- Variables SHOULD be initialized where they are declared and they SHOULD be declared in the smallest scope possible. A null initialization is acceptable.

- Variables MUST never have a dual meaning.

- Related variables of the same type CAN be declared in a common statement; unrelated variables SHOULD NOT be declared in the same statement.

- Variables SHOULD be kept alive for as short a time as possible.

- Loops / iterative declarations
	- Only loop control statements MUST be included in the "for" loop construction.
	- Loop variables SHOULD be initialized immediately before the loop; loop variables in a "for" statement MAY be initialized in the "for" loop construction.
	- The use of "do...while" loops is acceptable.
	- The use of "break" and "continue" is not discouraged.

- Conditionals
	- Complex conditional expressions SHOULD be avoided; use temporary boolean variables instead with proper naming.
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
			// always need a break keyword on the last case
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

### Whitespace

* Conventional operators MAY be surrounded by a space (including ternary operators).

* Commas SHOULD be followed by a space.

* Colons SHOULD be followed by a space.

* Semi-colons in for statements SHOULD be followed by a space.

* Semi-colons SHOULD NOT be preceded by a space.

* Function calls and method calls SHOULD NOT be followed by a space. Example: doSomething(someParameter); // NOT doSomething (someParameter)

* Logical units within a block SHOULD be separated by one blank line.

* Statements MAY be aligned wherever this enhances readability.
 
* Curly braket SHOULD have inner spaces. `var obj = { property: value, action: function }`


### Comments

* Tricky code SHOULD not be commented, but rewritten.

* All comments SHOULD be written in English.

* Comments SHOULD be indented relative to their position in the code, preceding or to the right of the code in question.

* The declaration of variables MAY be followed by a comment on the same line.

* Comments SHOULD be included to explain BLOCKS of code, to explain the point of the following block.

* Comments SHOULD NOT be included for every single line of code.


