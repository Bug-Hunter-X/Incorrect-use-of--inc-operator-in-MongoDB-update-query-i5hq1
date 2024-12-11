# Incorrect use of $inc operator in MongoDB update query
This example demonstrates an incorrect use of the `$inc` operator in a MongoDB update query. The `$inc` operator is used to increment a numeric field by a specified value.  However, in this case, a string ('1') is used instead of a number (1). This leads to an error because the `$inc` operator expects a numeric value.

## Bug
The bug lies in the following line of code:
```javascript
db.collection('myCollection').updateOne({ _id: ObjectId("someId") }, { $inc: { counter: '1' } });
```
The value '1' (a string) is provided to `$inc`, which is incorrect. 

## Solution
The correct way to use the `$inc` operator is to provide a numeric value:
```javascript
db.collection('myCollection').updateOne({ _id: ObjectId("someId") }, { $inc: { counter: 1 } });
```
This ensures that the `counter` field is incremented correctly by 1.