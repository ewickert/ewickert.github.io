---
layout: post
title: Stack based arithmetic
---

As of February 2016, Paxix does all of its arithmetic on the stack. This means
that the operation `2 + 2` is represented thus (in some generic assembly):

	push 2
	push 2
	pop $1
	pop $2
	add $1 $1 $2
	push $1

Memory accesses basically work the same way. That is y = 2 + x becomes:
	
	load $1 x 		// Move the contents of x into $1
	push $1
	push 2
	pop $1
	pop $2
	add $1 $1 $2 	//Add, store in $1
	push $1
	pop $1
	store y $1		//Store $1 in y


The obvious advantage of this system is that it is *much* easier for us, as the
compiler designers. Designing and implementing 
[register allocation](https://en.wikipedia.org/wiki/Register_allocation) is much
less fun then it would appear to be on first glance. The problem is that when
compared to the same addition performed with register arithmetic is much smaller:

	mov $1 2
	mov $2 2
	add $1 $1 $2

Even for the most trival example, the Paxix implementation takes twice as many
instructions. While this may not be a huge problem for what is currently a toy
langauge, it is still cause for concern. However, there we found two primary
advantages for the stack model.

### 1. Register Saving
On an x86_64 system, the caller is supposed to save `EAX`, `ECX`, and `EDX`. The
callee is supposed to save all of the other (approx. 1 billion) registers. Here
we gain the advantage of almost never having to save any registers. After every
operation, the value has been pushed onto the stack, and the registers can be
overwritten without fear.

### 2. Easy interpreter
One of the first design decisions we kicked around was whether we wanted a 
compiled or interpreted language. The answer to that turned out to be "why not
both?". When we eventually build an interpreted version of Paxix, the simple 
stack based operations will make it much simpler than a full blown architecture.

Of course, Paxix is an infant right now, and there's no telling where it will go.
It's not impossible, or even that unlikely that we will switch to a register 
oriented design in the future. Further, there are some obvious optimizations 
that can be implemented. As long as only two operands are used at a time, there
is no need to push them onto the stack. Every eliminated push eliminates a pop,
and suddenly our stack based arithmetic has become a simple register based 
system.
