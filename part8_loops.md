Loops
=====

Loops in bash are similar to other programming languages, they iterate over a list, collection or some sort of data structure. All loops have 3 main components:

  - Condition: there will be no iterations (and hence no work done) unless this is true when the loop starts
  - Unit of Work: the piece of work we want repeat every time the condition holds true. This is the body of the loop.
  - Exit clause: the trigger that allows us to stop doing the unit of work (otherwise we'll be there forever).

There are 3 kinds of loops in bash.

while loop
----------
The while loop is designed to do some piece of work given that a specific condition is met. On every iteration, a while loop basically runs an internal if statement to determine whether it should continue the next iteration or not.
	
	while [ some condition is true ]; do
		some work
	done
	
> **Important:** It is our responsibility to ensure the while loop has an exist clause. Our exist clause is usually the condition faling, but on occasions we can have manual forced intervention (we'll cover this in loop control)

Let's look at an example:

	apples=5
	while [ $apples -gt 0 ]; do 	# semicolon indicates there are 2 lines here
		echo "we have $apples apples, lets donate one"
		let apples=apples-1			# let is a bash builtin, like echo. THIS ALSO TRIGGERS OUR EXIST CLAUSE
	done

Lets break this down:
  - Condition: we have more than 0 apples. This loop will not do its piece of work unless we have more than zero apples
  - Unit of work: we echo how many apples we have, and programmatically donate one by subtracting it away.
  - Exit clause: we have zero or less apples: the fact that we subtract an apple on every iteration, we guarantee our exist.
  

for loop
--------
The `for` loop is designed to iterate over data structures. More specifically it iterates exactly the length of the data structure you are looping over, whilst providing you access to each item on each iteration via a local variable. Let's loop at an example:

	days_of_the_week=("Monday" "Tuesday" "Wednesday" "Thursday" "Friday" "Saturday" "Sunday")
	
	for day in ${days_of_the_week[@]}; do		
		echo $day						# day is out local variable that gives us access to each variable 
	done								# we're done. close the for loop
	
> **Task:** What are the 3 main components (condition, unit of work and exist clause) if the above example?
> **Task:** Can you rewrite the above `for` loop using a `while` loop? (this will let you see the 3 main components more clearly)