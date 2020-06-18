# Protocol Buffers Basics - I
		
###	first Message:

				in the first line `syntax = "proto3"`

###	Scalar types:

				numbers
				Boolean
				String - represented as `string` in Protobuf , must always contain utf-8
				Bytes
### Tags:

				In protocol buffers, field names are not important!(but when programming the fields are important)
				For protobuf the important element is the tag.
				smallest tag : 1
				largest tag: 2^29 -1 (= 536870911)
				we cannot use numbers 19000 to 19999 (because it's reserved by google for special use)
				Tags numbered from 1 to 15 use 1 byte in space {so use them frequently}.
				Tags numbered from 16 to 2047 use 2 bytes

### Repeated Fields:
				To make a `list` or an `array`, we can use the concept of repeated fields
				the list can take any numbers (0 or more) of elements we want
				the opposite of repeated is "singular" (we don't write it)
		>		example repeated type fieldname = number;  

### Comments:
				it's possible to add comments in our .proto file.
				it is recommended to use comments as a form of documentation of our schema.
				Comments can be of these two forms:
				?  // this is comment 
				? /* this is 
				?  * multiline comment */ 
		*  Default values for fields:
				this feature is introduced in protobuf 3.
				all fields, if not specified or unknown, will take a default value.
		>		the default value list		
						bool       			: false
						number(int32,...)	: 0
						string				: empty string
						bytes				: empty bytes
						emum				: first value
						repeated			: empty list
					
### Enums :
				the first value of an Enum is the default value.
				Enum's first value  must start by the tag 0(which is the default value) 
				! by convention we use all caps for the enum values {they don't have any type assigned to them} and tags values assigned to them.

# Protocol Buffers Basics II:

## Defining Multiple messages in the same file:
			it's possible , in the same .proto file	, to define multiple types.
			It is the super easy to reference them if we need to .

## Nesting types:
			it is possible to define types within types
			the reasons could be:
							avoiding naming conflicts
							enforcing some level of "locality" for that type
			we can nest types as deeply as we want.

## Import types:
			we can also have different types in different .proto file
			this is useful if we want to re-use code and import other .proto fields
			created by people in the team.

## Packages:
			it is very important to define the package in our protocol buffer messages live
				when your code gets compiled,it will be placed at the package you indicated.
				it also helps to prevent name conflict between messages (my.package.Person)
			Packages will help all the different languages compile correctly from .proto files (c#, c++, python,go, nodejs, etc..)	