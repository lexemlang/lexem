# Lexem Roadmap

This is the plan to work towards a 1.0.0 release. This is a "living document" and will be edited over time.

## Milestones

- [ ] Add support to re-parse lexemes.
- [ ] Add support to filter expressions.
  - [ ] Add filter lexeme.

## TODOs

```text
exp alfa(props![capture], arg0: def0, arg1: def1) {
	
}

alfa(a, arg1: b):[-capture]


keyword("alfa"):[-capture]
keyword(props![-capture], value: "alfa")


keyword("alfa")
keyword("alfa"):[]
keyword(null, value: "alfa")
keyword(props![], value: "alfa")


Selector node: @()
Selector to add: +@()
Selector to remove: -@()

name.property[property as x, condition]:action()


*					any name
name 				concrete name
!name 				no concrete name
(name, name2)		any of these names
!(name, name2)		none of these names

.property
.!property
[property: expression with property access]
[property as x: expression with property access]

:has()
:nth()

.property						existence
.!property						not existence
.property(expr with property)	existence and condition with access to property
.property(x: expr with x)		existence and condition with access to property as x
```