# API Best Practices

## Creating an order

When you create an order, you must properly update the record object you converted into an order.

1. Retrieve the record object using 'Update a record'.  
2. In the request body, add the `available` attribute with a value of `false`.

**Task Result**
The record object is properly updated.

## Cancelling an order 

When you cancel an order, you must properly update the record object you converted into an order.

1. Retrieve the record object using 'Update a record'.  
2. In the request body, add the `available` attribute with a value of `true`.

**Task Result**
The record object is properly updated.