## Cooperation Sync :

![[Coop Sync.png]]

## Competition Sync :

![[Comp Sync.png]]

## Dining Philosopher Problem :

```cpp
// Initialize 5 semaphores to 1 (available) 
Semaphore forks[5] = {1, 1, 1, 1, 1}

Philosopher(i):
    while true:
        Think()
        
        // Philosopher 4 is the exception (Asymmetric)
        // They sit between fork 4 and fork 0.
        
        if i == 4:
            wait(forks[0])       // Pick up lower-numbered fork first
            wait(forks[4])       // Pick up higher-numbered fork second
        
        // Philosophers 0, 1, 2, and 3 follow the standard order
        // They sit between fork i and fork i+1.
        
        else:
            wait(forks[i])       // Pick up lower-numbered fork first (left)
            wait(forks[i + 1])   // Pick up higher-numbered fork second (right)
            
        Eat()
        
        // Put down both forks (order of putting down doesn't matter for deadlock)
        signal(forks[i])
        signal(forks[(i + 1) % 5])
```

- Philosopher 4 should wait until 0th fork free,which leaver fork 4 free which shall be picked by 3 to complete ultimately avoiding deadlock.

## Message Passing Rendezvous:

- When a sender task’s message is accepted by a receiver task, the actual message transmission is rendezvous.

## Functional Programming Languages:

- In an FPL, variables are not necessary, as is the case in mathematics

- Referential Transparency - In an FPL, the evaluation of a function always produces the same result given the same parameters

- A program has the property of referential transparency if any two expressions in the program that have the same value can be substituted for one another anywhere in the program, without affecting the action of the program.

- A side effect occurs when a function does something other than just returning a value, like modifying a global variable, printing to a screen, or updating a database.When side effects are present, you lose referential transparency.

## Primitive Functions & Lambda Expressions:

![[Primitive&lambda.png]]

## Numeric Predicate Functions:

![[Numeric Predicate FN.png]]

## COND :

![[COND eg.png]]

## Quote :

- QUOTE - takes one parameter; returns the parameter without evaluation

- QUOTE is required because the Scheme interpreter, named EVAL, always evaluates parameters to function applications before applying the function. QUOTE is used to avoid parameter evaluation when it is not appropriate

- '(A,B) is equivalent (Quote(A,B))

-  Lists in LISP and Scheme are delimited by parentheses and use no commas (A B C D) and (A (B C) D)

-  Data and code have the same form As data, (A B C) is literally what it is As code, (A B C) is the function A applied to the parameters B and C

- The interpreter needs to know which a list is, so if it is data, we quote it with an apostrophe ′(A B C) is data

## List Operations : 

![[List Operations.png]]

![[Examples of list op.png]]

## Predicate Functions : 

![[Predicate Functions.png]]

## e.g :

```LISP
(DEFINE (equalsimp list1 list2)
(COND
	((NULL? list1) (NULL? list2))
	((NULL? list2) #F)
	((EQ? (CAR list1) (CAR list2))
		(equalsimp(CDR list1)(CDR list2)))
	(ELSE #F)
))
```

```LISP
(DEFINE (member atm a_list)
(COND
	((NULL? a_list) #F)
	((EQ? atm (CAR a_list)) #T)
	((ELSE (member atm (CDR a_list)))
))
```

```LISP
(DEFINE (equal list1 list2)
(COND
	((NOT (LIST? list1))(EQ? list1 list2))
	((NOT (LIST? list2)) #F)
	((NULL? list1) (NULL? list2))
	((NULL? list2) #F)
	((equal (CAR list1) (CAR list2))
		(equal (CDR list1) (CDR list2)))
	(ELSE #F)
))
```

```LISP
(DEFINE (append list1 list2)
	(COND
		((NULL? list1) list2)
		(ELSE (CONS (CAR list1)
			(append (CDR list1) list2)))
))
```

```LISP
(DEFINE (LENGTH LST)
	(IF (NULL? LST) 0
	(+ 1 (LENGTH (CDR LST)))))


(DISPLAY (LENGTH '(A B C)))
```

```LISP
(DEFINE (REVERSE LST)
	(IF (NULL? LST) ‘()
	(APPEND (REVERSE (CDR LST)) (LIST (CAR LST)))))


(DISPLAY (REVERSE '(1 2 3)))
```

```LISP
(DEFINE (quadratic_roots a b c)
  (LET (
        (root_part_over_2a (/ (SQRT (- (* b b) (* 4 a c))) (* 2 a)))
        (minus_b_over_2a   (/ (- 0 b) (* 2 a)))
       )
    (LIST
      (+ minus_b_over_2a root_part_over_2a)
      (- minus_b_over_2a root_part_over_2a))))
```

## Tail Recursion :

- A function is tail recursive if its recursive call is the last operation in the function

- A tail recursive function can be automatically converted by a compiler to use iteration, making it faster

Original:
  
```LISP
(DEFINE (factorial n)
	(IF (<= n 0)
		1
	(* n (factorial (- n 1)))
))
```

Tail Recursive :
  
```LISP
(DEFINE (facthelper n factpartial)
	(IF (<= n 0)
		factpartial
	facthelper((- n 1) (* n factpartial)))
))

(DEFINE (factorial n)
	(facthelper n 1))
```

Eg. Reverse a list (Tail-Recursive):

```LISP
(define (my-reverse lst)
	(define (reverse-helper remaining result)
		(if (null? remaining)
			result
	(reverse-helper (cdr remaining) (cons(car remaining) result))))

(reverse-helper lst '()))
```

## Subtypes vs Subclasses 

### Subclass (Focuses on Code Reuse): 
   - A subclass inherits the implementation (the actual code) from a parent class

Ex :
```java
class Animal {    
    void speak() {           
        System.out.println("Animal makes a sound"); 
    } 
}

class Dog extends Animal {        
    void speak() {            
        System.out.println("Dog barks"); 
    }
}
// Dog is a SUBCLASS of Animal. 
// It inherits the structure of Animal to reuse code, but provides its own specific implementation for speak().
```

### Subtype (Focuses on Behavior): 
   - A subtype inherits the interface and behavior (the rules) of a parent. 
   - You use it when you want to guarantee that a new object can safely replace a parent object without breaking the program.

Ex :
```java
interface Swimmer {
    void swim(); 
}

class Fish implements Swimmer {
    @Override
    public void swim() {
        System.out.println("Fish is swimming...");
    }
}
// Fish is a SUBTYPE of Swimmer. 
// It guarantees the expected behavior without inheriting any actual code.
```

## Exception Handling

- **Exception** :  Any unusual event, erroneous or not,that is detectable by either hardware or software and that may require special processing.
## Reflection

A program can inspect and use its own classes,methods, and objects during runtime.

