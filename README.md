# Milestones - The Thinking Tasks Scheduler

Milestones is Clojure library which processes tasks with constraints
in order to generate automatic schedules based on some parameters for
making decisions on sorting.

Tasks are basically a map containing ids as keys and information about
the tasks as values (maps). Here is an example :

	{ 1 { :task-name "A description about this task" :resource-id 2 :duration 5 :priority 1 }

	  2 {:task-name "A description about this task" :resource-id 1 :duration 4 :priority 1 :predecessors [1]} }

Milestones tries to detect any circular dependencies, that is, tasks
that depend on themselves or on tasks that end up depending on
themselves, actually, the tasks definition must be a directed non
cyclical graph.

Special tasks with spcial user :milestone are milestones, i.e, they only have ids, descriptions and predecessors, and last 
0 time units.

The output of Milestones is a schedule, that is, if it's possible, the
tasks map, with a :begin field, telling us when to begin each task.
	
	{ 1 { :task-name "A description about this task" :resource-id 2
		:duration 5 :priority 1 **:begin 0**}

	  2 {:task-name "A description about this task" :resource-id 1
        :duration 4 :priority 1 :predecessors [1] **:begin 5**}}


## Usage

TODO

## History

The concept of auto-magic project scheduling is inspired from **the great**
[Taskjuggler](http://www.taskjuggler.org). 

A first prototype of Milestones was built as an entry to the Clojure
Cup 2014. You can find the code and some technical explanation of the
algorithms in use (core.async, etc...) 
[here](https://github.com/turbopape/milestones-clojurecup2014).

Although the protorype included the module for interpreting tasks
written in natural english, Milestones the actual project will focus
on scheduling. The Tasks interpreter and the Tasks renderer are
projects of their own right.

## License

Copyright © 2014 rafik Naccache and Contributors.

Distributed under the GNU GPL v3.

All used Libraries in this project (see project.clj) pertain to their
respective authors and their respective licenses apply.
