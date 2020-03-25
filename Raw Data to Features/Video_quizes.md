1. Which of these features are related to the objective?
_Objective: Predict total number of customers who will use a certain discount coupon_

* __Font of the text with which the discount is advertised on partner websites__
* __Price of the item the coupon applies to__
* Number of items in stock


2. Which of these features are related to the objective?
_Objective: Predict point-of-sale credit card fraudulent activity_

* __Whether cardholder has purchased these items at this store before__
* Credit card chip reader speed
* __Category of item being purchased__
* Expiry date of credit card


3. Why is the second a bad feature? What could go wrong? Hint: what happens if the cluster ID was taken from another model? What if that model updates without telling you? Will you still be able to learn anything from your training data?

__Whats wrong with the second Feature ?__
1. city_id:"br/sao_paolo"
2. inferred\_city\_cluster\_id : 219
Answers options -
* Feature definitions should not change over time
* Ambiguous feature field values could cause issues
* "inferred" seems to imply this field could come from another system which we may not have knowledge or control over the city-value mappings
* __All of the above are correct__


4. Are these features knowable at prediction time?
_Objective: Predict total number of customers who will use a certain discount coupon_
* Total number of discountable items sold
* __Number of discountable items sold the previous month__
* __Number of customers who viewed ads about item__


5. Are these features knowable at prediction time?
_Objective: Predict whether a credit card transaction is fraudulent_
* __Whether cardholder has purchased these items at this store before__ _Yes - but you have to define the time window very carefully because point-of-sale data may have a delay in getting to your data analytics warehouse._
* __Whether item is new at store (and can not have been purchased before)__
* __Category of item being purchased__
* __Online or in-person purchase__
