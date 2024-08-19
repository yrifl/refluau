# Standard Lua

Standrad syntax writing on lua, compatible with Luau.

## Comments

```luau
-- Comment

--[[ Multiline
     comment ]]
```

## Variables

```luau
local x = 2
local three, four = 3, 4
two, four = 2, 4
```

## Conditionals

```luau
if condition then
    print("yes")
elseif condition2 then
    print("maybe")
else
    print("no")
end
```

## Invoking functions

```luau
print()
print("Hi")

-- You can omit parentheses if the argument is one string or table literal.

print "Hello, World" --> print("Hello, World")
f(x = 10, y = 20)    --> f({x = 10, y = 20})
type {}              --> type({})

-- The same
print [[a multi-line
    message]]
print([[a multi-line
    message]])

-- Errors
local x = "hello"

print x             --> Errors

```

## Tables / Arrays

```luau
t = {}
t = { a = 1, b = 2}
t.a = function()
    -- stuff
end

-- The same:
t = { ["x"] = 200 }
t = { x = 200}

t.x

-- Remember, arrays are also tables
array = { "a", "b", "c", "d" }

print(array[2]) -- "b" (one-indexed)
print(#array)   -- 4 (length of table / array)
```

## Functions

```luau
function myFunction()
    return 1
end

function myFunctionWithArgs(a, b)
    -- ...
end

anotherFunction = function()

end

anotherFunction()

-- Not exported in the module (private functions)
local function myPrivateFunction()
    -- ...
end

-- Splats
function doAction(action, ...)
    if action == 'write' then
        print(...)
    end
end

doAction('write', "Stupid", "Bob")
```

## Loops

```luau
-- Checking condition if it's true keep running
while condition do
    -- ...
end

-- Iterate over 1 through 5, i = { 1, 2, 3, 4, 5}
for i = 1, 5 do
    -- ...
end

-- Iterate table (tab) with (k) as index and (v) as value
for k, v in pairs(tab) do

end

-- Runs codeblock first before checking condition
repeat 
    print "Wait"
until conditon

-- Breaking out:
while x do 
    if condition then 
        break
    end
end
```

## Lookups

```luau
prototype = { x = 2, y = function()
    -- ...
end}

-- The same:
prototype.x
prototype['x']

-- Syntatic sugar, there are equivalent:
prototype.y(prototype)
prototype:y()

prototype.y(prototype, a, b)
prototype:y(a, b)

function a:y(z)
    self.bla
end

function a.y(self, z)
    self.bla
end
```

## Logic

```luau
-- Logic (and/or)

not true        --> false
not false       --> true
not nil         --> true
not 0           --> false
not not nil     --> false

--[[ (and)
If the left hand of the expression is not nil or false then the right hand is picked. Otherwise the left hand is picked.
]]

0 and 20        --> 20
21 and 20       --> 20
-1 and 10       --> 10
nil and 20      --> nil
false and nil   --> false
nil and false   --> nil

--[[ (or)
If the left hand of the expression is not nil or false then the left hand is picked. Otherwise the right hand its picked.
]]

4 or 5          --> 4
6 or 4          --> 6
nil or 13       --> 13
false or nil    --> nil
nil or false    --> false

-- * note: logical operators consider false and nil as false and anything else as true.
```
