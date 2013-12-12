## Normal Forms
### First normal form 
..*All attributes must be atomic, and no repeating groups
	..* Eliminate multi-valued attributes, and Eliminate repeated attributes
### Second normal form 
..*  First normal form, and no partial functional dependencies
	..* Eliminate subkeys (where the subkey is part of a composite primary key)
### Third normal form 
..* Second normal form, and no transitive functional dependencies
	..* Eliminate subkeys (where the subkey is not part of the primary key)

### Recursive Association
..* Connects a single class type (serving in one role) to itself (serving in another role).

### Data Integrity
..* Insuring that the value entered in each field of a table is consistent with its attribute domain.

### Union
..* This includes members of either or both sets with no duplicates.

### Minus or Except
..* This includes only those members of the set on the left side of the expression that are not contained in the set on the right side of the expression. 

### Intersect
..* This includes members that are common to both sets.

### Union All
..* This works like UNION, except it keeps duplicate rows in the result.

### Set Operations
..* In order to do this all tables must have to contain the same number of objects of the same type.

### Weak Entity
..* This is considered a class within a class. 

### Multi-valued Attribute
..* There are many distinct values entered for this in the same column of the table. 

### Repeated Attribute
..* This causes a large number of null values in a table row. 

### Show the repeating attribute in its own class
..* You would do this when the repeated attribute has only several attributes of its own.

### Subclass
..* You have this when one or more attributes of a class are characteristics of only some individuals of that class, but not of others. 

### Superclass 
..* Sometimes, instead of finding unique attributes in a single class type, you might find two or more classes that have many of the same attributes. Make a superclass.

### Specialization
..* This is the process of designing subclasses from “top down”. 

## Specialization Constraints

###  Incomplete Specialization (Partial)
..* Only some individuals of the parent class are specialized (that is, have unique attributes). Other individuals of the parent class have only the common attributes.

### Complete Specialization
..* all individuals of the parent class have one or more unique attributes that are not common to the generalized (parent) class.

### Disjoint Specialization (Exclusive)
..* An individual of the parent class may be a member of only one specialized subclass.

### Overlapping Specialization
..* an individual of of the parent class may be a member of more than one of the specialized subclasses.

_____________________________________________________________________________________________________________

### Aggregation
..* This is the UML notation to indicate that a class type really represents a collection of individual components.

### Composition
..* This is a stronger form of aggregation that indicates component instances cannot exist on their own without a parent.

### Specialization Constraints
..* The subclass association line is labeled with these. One example is “incomplete”.

### Data Integrity
..* One goal of database developers is to provide this, part of which means insuring that the value entered in each field of a table is consistent with its attribute domain.

### Validation Rule
..* Sometimes we can devise one of these to separate good from bad data 

### Enumerated Domains
..* Attribute domains that may be specified by a well-defined, reasonably-sized set of constant values are called this.

### Stereotype
..* is an example of this UML notation.

### Enumeration Class
..* This type of class is unique because it lists values of the attribute (in quotes), rather than attribute names. 

### Enumerated Domains
..* Attribute domains that may be specified by a well-defined, reasonably-sized set of constant values

### Normalization
..* This is a process of applying a set of rules to your database design, mostly to achieve minimum redundancy in the data. 

### Second Normal Form
..* This normal form eliminates subkeys where the subkey is part of a composite primary key.

### Third Normal Form
..* This normal form eliminates subkeys where the subkey is not part of the primary key.

### First Normal Form
..* This normal form eliminates multi-values attributes and repeated attributes.  

### Denormalization
..* This means to “break the rules” of database design in order to accommodate other parts of a system. 

## Transactions

### Concurrency
..* The goal in a ‘concurrent’ DBMS is to allow multiple users to access the database simultaneously without interfering with each other.

### Commit
..*Any changes made during the transaction by this transaction are committed to the database.

### Abort
..*All the changes made during the transaction by this transaction are not made to the database. The result of this is as if the transaction was never started.
	#### Reasons for Abort
	..* System crash
	..* Transcation aborted by system
		..* Execution cannot be made atomic (a site is down)
		..* Execution did not maintain database consistency (integrity constraint is violated)
		..* Execution was not isolated
		..* Resources not available (deadlock)
	..* Transaction requests to roll back

### Schedules
..* A transaction schedule is a tabular representation of how a set of transactions were executed over time. This is useful when examining problem scenarios. Within the diagrams various nomenclatures are used:
	..* READ(a) - This is a read action on an attribute or data item called ‘a’.
	..* WRITE(a) - This is a write action on an attribute or data item called ‘a’.
	..* WRITE(a[x]) - This is a write action on an attribute or data item called ‘a’, where the value ‘x’ is written into ‘a’.
	..* tn (e.g. t1,t2,t10) - This indicates the time at which something occurred. The units are not important, but tn always occurs before tn+1.

## ACID
..* The execution of each transaction must maintain the relationship between the database state and the enterprise state

### Atomicity
	..* Transaction is either performed in its entirety or not performed at all.
### Consistency
	..* Transaction must take the database from one consistent state to another. 
### Isolation
	..* Transaction should appear as though it is being executed in isolation from other transactions.
### Durability
	..* Changes applied to the database by a committed transaction must persist, even if the system fails before all changes reflected on disk.

### Atomicity
..* A real-world event either happens or does not happen
	..* Student either registers or does not register
..* Similarly, the system must ensure that either the corresponding transaction runs to completion or, if not, it has no effect at all
	..* Not true of ordinary programs.  A crash could leave files partially updated on recovery
..* How is atomicity achieved?
	..* Logging

### Consistency
..* Consistency of the database is guaranteed by constraints and triggers declared in the database and/or transactions themselves

### Isolation
..* Serial Execution:  transactions execute in sequence 
	..* Each one starts after the previous one completes.
		..* Execution of one transaction is not affected by the operations of another since they do not overlap in time
	..* The execution of each transaction is isolated from   all others.
..* If the initial database state and all transactions are consistent, then the final database state will be consistent and will accurately reflect the real-world state, but
..* Serial execution is inadequate from a performance perspective

### Durability
..* The system must ensure that once a transaction commits, its effect on the database state is not lost in spite of subsequent failures
..* Effects of committed transactions must survive DBMS crashes
..* How is durability achieved?
	..* DBMS manipulates data in memory; forcing all changes to disk at the end of every transaction is very expensive
	..* Logging
#### Implementing Durability
..* Database stored redundantly on mass storage devices to protect against media failure
..* Architecture of mass storage devices affects type of media failures that can be tolerated
..* Related to Availability:  extent to which a (possibly distributed) system can provide service despite failure
	..* Non-stop DBMS (mirrored disks)
	..* Recovery based DBMS (log)

### Serializability
..* A ‘schedule’ is the actual execution sequence of two or more concurrent transactions.
..* A schedule of two transactions T1 and T2 is ‘serializable’ if and only if executing this schedule has the same effect as either    T1;T2 or T2;T1.

### Precedence Graph
..* In order to know that a particular transaction schedule can be serialized, we can draw a precedence graph. This is a graph of nodes and vertices, where the nodes are the transaction names and the vertices are attribute collisions.
..* The schedule is said to be serialized if and only if there are no cycles in the resulting diagram.
