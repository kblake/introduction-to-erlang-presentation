!SLIDE incremental commandline

#Shell

<br /><br />
<br /><br />

	$ erl

	Eshell V5.8  (abort with ^G)
	1> 1 + 1.
	2



!SLIDE bullets

#Variables

	@@@ ruby
	X = 10. 
	Y = "john".
	Z = 3.14.



!SLIDE bullets incremental

#Pattern matching

* = looks like an assignment operator but 
* it is really a pattern matching operator
* X is unbound
* X = 10 is bound
* can only bind a variable once


!SLIDE

#Pattern matching

	@@@ ruby
	X.
	variable X is unbound

	X = 2 + 4.
	X = 6.
	X = 3 + 3.
	X = 6 + 0.
	X = 5 + 1.
	X = 6 * 1.



!SLIDE

#Erlang

##Non numeric constant value<br />
##Start with lower case letter<br /><br />

	@@@ ruby
	Temp = hot.
	Age = old.
	


!SLIDE

#Tuple

##Convention is to use a meaningful atom that represents the data that follows<br /><br />


	@@@ ruby
	Person = {person, {name, "john"}, {age, 99}}.

!SLIDE

#More Pattern Matching

	@@@ruby
	%extracting values out of a tuple

	Point = {point, 10, 45}.
	{point, X, Y} = Point.
	
	%10 is bound to X
	%45 is bound to Y
	%point, well is just a point
	

	
!SLIDE

#List

	@@@ ruby
	Numbers = [1, 2, 3].
	Information = ["john", 99, blue].
	ShoppingList = [{bananas, 10}, {milk, 2}].

!SLIDE bullets incremental

#Getting values out of a list

* **head** is the first item in the list
* **tail** is the rest of the list

!SLIDE bullets incremental

#Getting values out of a list

	@@@ruby
	Nums = [1,2,3,4,5]
	[Head|Tail] = Nums.
	% Head has the value of 1
	% Tail has the rest	[2,3,4,5]

	[Head2|Tail2] = Tail.
	% Head2 has the value of 2
	% Tail2 has the rest [3,4,5]

	


!SLIDE smaller

#Functions

	@@@ruby
	-module(geometry).
	-export([area/1]).

	area({rectangle, Base, Height}) -> Base * Height;
	area({circle, Radius}) -> 3.14 * Radius * Radius;
	area({triangle, Base, Height}) -> area({rectangle, Base, Height})/2.

	%call the code elsewhere

	geometry:area({rectangle, 4, 5}).
	geometry:area({circle, 4}).
	geometry:area({triangle, 4, 5}).

!SLIDE incremental bullets

#Calling the correct clause

* no conditionals
* pattern match arguments

!SLIDE center

![functions pattern matching](functions-pattern-matching.jpg)

!SLIDE center

![functions pattern matching](circle-match.jpg)


!SLIDE center

![functions pattern matching](triangle-match.jpg)




!SLIDE smaller

#Anonymous functions

<br /><br />

	@@@ruby
	Triple = fun(X) -> 3 * X end.
	Triple(10).
	
	UpIt = fun({double, Num}) -> 2 * Num; 
		    ({triple, Num}) -> 3 * Num 
			end.
	Upit({double, 10}).
	UpIt({triple, 10}).

	%more pattern matching


!SLIDE smaller

#Map and List Comprehension

<br /><br />

	@@@ruby
	Numbers = [1,2,3,4,5].

	%Built-in Function (BIF)
	lists:map(fun(Number) -> Number * 2 end, Numbers).

	%Use list comprehension
	[2 * Number || Number <- Numbers].
