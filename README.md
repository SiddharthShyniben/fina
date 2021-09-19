# fina

```fina
# This is a comment

# key value pairs
title = fina

# lists
list:
	- fast # that's a string
	- 42 # a number
	- true # a boolean
	-
		- nested # list!
		- 42
		- 'cool!' # Quotes if you like
		- yeah, you can add spaces or 's etc.

# C like list, if you (c)like
list = [
	fast,
	42,
	true,
	[nested, 42, cool]
]

# objects
object:
	key = val
	more = stuff

	list-again:
		- foo
		- bar
		- baz
		- quux
```

`fina` is a simple configuration file format which is very simple to write and understand.
It takes lessons from YAML, TOML, and more formats, combining their ideas into a powerful but simple syntax.

## Why a new format?

There are many problems with other formats.

TOML, while being powerful, is very verbose. It is also sometimes _too_ powerful for simple uses.
`fina` doesn't go overboard and has five types: string, number, boolean, object, and array.

YAML is also a pretty good format, but it's not strict. There are 22 ways to write a boolean.
In YAML, if you write `4:30` as a value, the output will be 270(!).
YAML is also pretty confusing when it comes to whitespace (atleast for me).
There are times when YAML can [break because of a single line break](https://github.com/IronScheme/IronScheme/commit/2f847793946935bd9143cdfb064f9006f763df68)

## Spec

The spec is a WIP

## Complete example

```fina

##########
# BASICS #
##########

key = value
string = str
number = 42
more-numbers = 3.14
bools = [yes, true, no, false]
"key can be quoted for more characters" = yes
"unquoted keys may contain" = "[A-Za-z0-9_-]"

##########
# STRING #
##########

string = This is a string. There's no difference between ' and " and no quotes at all (most of the time)

# No multiline strings. Convince me that there is a use case for it, and I'll add it.
# If you need it, just use '\n'

##########
# NUMBER #
##########

# Numbers can be either integers or floats
life = 42
negative-life = -42
pi = 3.14159

# Use , to seperate the digits if you like
googol = 10,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000,000

###########
# BOOLEAN #
###########

# Use yes, no, true, or false for booleans

really = yes
maybe = no

# Quote them to escape
string = "yes"

########
# LIST #
########

list:
	- one
	- two
	- three
	-
		- 42
		- life

# clike
list = [this, is, 1, list,
		whitespace, dont, matter
		mix, 42, true, yes,
		[more, "this is a comma: ,"]]

# If you specify a list twice, items will be added

stuff = [foo]
# ...
stuff = [bar]

# Now stuff is [foo, bar]

##########
# OBJECT #
##########

# syntax almost the same as a list...
object:
	# Add any key value pairs
	foo = bar

	life = 42

# They can be empty
empty:

you:
	can:
		nest:
			them = true

# clike

this = {can = be, clike = {really: true}}

# like earlier, objects are merged
obj:
	foo = true
	bar = 'yes'
# ...
obj:
	foo = false
	baz = 'new!'

# now, obj is:
# obj:
# 	foo = false
# 	bar = 'yes'
# 	baz = 'new'
```

## Implementations

None yet.
