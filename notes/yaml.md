#YAML

https://www.c-sharpcorner.com/article/the-basics-of-yaml-in-5-minutes-or-less/

## What
YAML is a data-orientated human readable serialisation language.
YAML is an acronym for 'Yet Another Markup Language', or more commonly 'YAML Ain't Markup Language'

A YAML file is constructed of a number of different elements.
YAML elements are mostly based on Key-Value pairs.
YAML is a superset of JSON, so we can utilise JSON style sequences and maps in constructs.

* Spaces/Indenting 
In YAML, you indent with spaces, not tabs. 
These **MUST** be spaces betwen element parts.
eg.
Key: Value <- GOOD
Key:Value <- BAD

* Begin/End document
Optional.
To start a document insert '---' at the top, 
to end a document insert '...'

* Comments
# Comments are made like this

* Scalar
key: value
someNumber: 299
quotedText: "some text description"
moreQuotedtext: strings do not have to be quoted, but I prefer to do it=
boolean: true
we can also have spaces in keys: and also in values
nullKeyValue: null

* Collections & Lists
List and collection members are lines that begin at the same indentation level, starting with a dash followed by a space.
Fancy-Cars
- Porsche
- Aston Martin
- Bentley

* Multi-line collections
Complex keys can be catered for by placing a question mark follow by a pipe symbol to flag the start of a complex key:
? |
starting a complex
key with many
lines
: and i am the value!

* Nested Collections
You can also have deep nested collections
# Car information
- Driver
name: Francis Black
age: 21
Driving license type:
- full car license
- racing license formula V : details
license id: ABC12345
expiry date: 2017-12-28

* Dictionaries
CarDetails:
make: Porsche
model: 911
fuel: Petrol
