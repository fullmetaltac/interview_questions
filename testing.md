# Table of Contents
- [Table of Contents](#table-of-contents)
    - [Automation QA](#automation-qa)
    - [Manual QA](#manual-qa)
    - [References:](#references)

### Automation QA

>🔹***What is xpath used for in TA?***

XPath uses path expressions to select nodes or node-sets in an XML document. 

[xpather.com](http://xpather.com/) - online tool

```xml
<!--xml sample-->
<root xmlns:foo="http://www.foo.org/" xmlns:bar="http://www.bar.org">
	<actors>
		<actor id="1">Christian Bale</actor>
		<actor id="2">Liam Neeson</actor>
		<actor id="3">Michael Caine</actor>
	</actors>
	<foo:singers>
		<foo:singer id="4">Tom Waits</foo:singer>
		<foo:singer id="5">B.B. King</foo:singer>
		<foo:singer id="6">Ray Charles</foo:singer>
	</foo:singers>
</root>
```

:bulb: *Examples:*

- `//*` &rarr; all the elements in the document

- `/root/actors/actor` &rarr;
```xml
<!--result-->
		<actor id="1">Christian Bale</actor>
		<actor id="2">Liam Neeson</actor>
		<actor id="3">Michael Caine</actor>
```
- `//foo:singer` &rarr;
```xml
<!--result-->
		<foo:singer id="4">Tom Waits</foo:singer>
		<foo:singer id="5">B.B. King</foo:singer>
		<foo:singer id="6">Ray Charles</foo:singer>
```

- `//foo:singer/@id` &rarr;
```xml
<!--result-->
                    id="4"
                    id="5"
                    id="6"
```

- `//actor[1]/text()` &rarr;
```xml
<!--result-->
                    Christian Bale
```

- `//actor[last()]` &rarr;
```xml
<!--result-->
		<actor id="3">Michael Caine</actor>
```

- `//actor[position() < 3]` &rarr;
```xml
<!--result-->
		<actor id="1">Christian Bale</actor>
		<actor id="2">Liam Neeson</actor>
```

- `//actor[@id>=2]` &rarr;

```xml
<!--result-->
		<actor id="2">Liam Neeson</actor>
		<actor id="3">Michael Caine</actor>
```

- `/root/foo:singers/*` &rarr;

```xml
<!--result-->
		<foo:singer id="4">Tom Waits</foo:singer>
		<foo:singer id="5">B.B. King</foo:singer>
		<foo:singer id="6">Ray Charles</foo:singer>
```



- `//actor|//foo:singer` &rarr;

```xml
<!--result-->
		<actor id="1">Christian Bale</actor>
		<actor id="2">Liam Neeson</actor>
		<actor id="3">Michael Caine</actor>
		<foo:singer id="5">B.B. King</foo:singer>
		<foo:singer id="6">Ray Charles</foo:singer>
```

-  `//singer[@id=5]/preceding-sibling::*` &rarr;

```xml
<!--result-->
		<foo:singer id="4">Tom Waits</foo:singer>
```

- `//singer[@id=5]/following-sibling::*` &rarr;

```xml
<!--result-->
		<foo:singer id="6">Ray Charles</foo:singer>
```

### Manual QA

### References:

---