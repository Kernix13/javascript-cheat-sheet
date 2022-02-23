# Objects

## Object methods

Object.keys():	Returns an array containing the names of all of the given object's own enumerable string properties.
Object.values():	Returns an array containing the values that correspond to all of a given object's own enumerable string properties

Object.prototype.toString()	Returns a string representation of the object.
Object.prototype.valueOf()	Returns the primitive value of the specified object.
Object.prototype.hasOwnProperty()	Returns a boolean indicating whether an object contains the specified property as a direct property of that object and not inherited through the prototype chain.

There are three native ways to list/traverse object properties:

for...in loops. This method traverses all enumerable properties of an object and its prototype chain.
Object.keys(o). This method returns an array with all the own (not in the prototype chain) enumerable properties' names ("keys") of an object o.
Object.getOwnPropertyNames(o). This method returns an array containing all own properties' names (enumerable or not) of an object o.

Defining getters and setters
A getter is a method that gets the value of a specific property. A setter is a method that sets the value of a specific property. You can define getters and setters on any predefined core object or user-defined object that supports the addition of new properties.

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects
