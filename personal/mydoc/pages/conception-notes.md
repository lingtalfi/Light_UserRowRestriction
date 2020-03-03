Light_UserRowRestriction, conception notes
==========
2020-02-28


This is a simple implementation of a defense mechanism to the [database-identity-usurpation](https://github.com/lingtalfi/TheBar/blob/master/discussions/database-identity-usurpation.md) problem.

Our service basically implements the guidelines suggested in the ["A possible defense mechanism in light" section](https://github.com/lingtalfi/TheBar/blob/master/discussions/database-identity-usurpation.md#a-possible-defense-mechanism-in-light).


We introduce a new concept though, the concept of row restriction.

Basically, the plugins author can add the restrictions they want.

A restriction restricts a certain operation to be applied on a given row of a given table.

We use the four "crud" operations (create, read, update, delete), the replace method will use the update operation.


The restriction can be thought as a function that returns a boolean to the question: is the current user allowed to do the
given operation on the given table (and the given parameters).

The answer to this question is subjective and defined by the (subscribers of our service) plugins. 
  
  
This "restriction" system allows us to encapsulate the problems into the aforementioned function, problems such as:

- is the current user some kind of admin? In which case he/she might be considered an owner too
- is the read operation allowed for this particular table (which might/might not contain confidential info), or the delete operation, etc...


