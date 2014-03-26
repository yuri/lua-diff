
A simple diff of two strings:
```lua
> diff = require("diff")
> for _, token in ipairs(diff.diff("This is a test", "This was a test!")) do 
>> print(token[1], token[2])
>> end
This    same
is      out
was     in
        same
a       same
        same
test    out
test!   in
        same
```
Even simpler:
```lua
cmp = diff('This is a test', 'This was a test')
> = cmp:format_as_text()
This -{is}+{was} a test
```


That is, `diff.diff(old, new)` returns a table of pairs, each consisting of a string
and it's status: "same" (the string is present in both), "in" (the string appeared
in _new_, or "out" (the string was present in _old_ but was removed).

Alternatively, you can just generate an HTML for this diff:
```lua
cmp = diff('This is a test', 'This was a test')
> = cmp:format_as_html()
This <del>is</del><ins>was</ins> a test

```
