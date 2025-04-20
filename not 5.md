set 1 hello1
set 2 hello2

get 1
get 2

shutdown save

get 1
get 2

set 3 hello3
get 3

shutdown nosave
get 3
get 1
get 2

set name1 "John"
set name2 "Doe"

get name1
get name2

<b><mark>rename name1 fname</mark></b><br>
get name1
get fname

rename name2 lname
get name2
get lname

rename 11 abc


rename fname lname
get fname
get lname


set k1 v1
set k2 v2

get k1
get k2

<b><mark>renamenx k1 k2</mark></b><br>

get k1
get k2

renamenx k1 k3
get k1
get k3




