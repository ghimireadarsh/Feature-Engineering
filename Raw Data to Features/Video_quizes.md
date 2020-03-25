1. Which of these features are related to the objective?
_Objective: Predict total number of customers who will use a certain discount coupon_

* __Font of the text with which the discount is advertised on partner websites__
* __Price of the item the coupon applies to__
* Number of items in stock
______________________________________________________________________________________

2. Which of these features are related to the objective?
_Objective: Predict point-of-sale credit card fraudulent activity_

* __Whether cardholder has purchased these items at this store before__
* Credit card chip reader speed
* __Category of item being purchased__
* Expiry date of credit card
______________________________________________________________________________________

3. Why is the second a bad feature? What could go wrong? Hint: what happens if the cluster ID was taken from another model? What if that model updates without telling you? Will you still be able to learn anything from your training data?

__Whats wrong with the second Feature ?__
1. city_id:"br/sao_paolo"
2. inferred\_city\_cluster\_id : 219
Answers options -
* Feature definitions should not change over time
* Ambiguous feature field values could cause issues
* "inferred" seems to imply this field could come from another system which we may not have knowledge or control over the city-value mappings
* __All of the above are correct__
______________________________________________________________________________________

4. Are these features knowable at prediction time?
_Objective: Predict total number of customers who will use a certain discount coupon_
* Total number of discountable items sold
* __Number of discountable items sold the previous month__
* __Number of customers who viewed ads about item__ _Yes - but keep in mind you may not have real-time or very recent data on your customers until your ads system pushes the data to your data warehouse._
_______________________________________________________________________________________

5. Are these features knowable at prediction time?
_Objective: Predict whether a credit card transaction is fraudulent_
* __Whether cardholder has purchased these items at this store before__ _Yes - but you have to define the time window very carefully because point-of-sale data may have a delay in getting to your data analytics warehouse._
* __Whether item is new at store (and can not have been purchased before)__
* __Category of item being purchased__
* __Online or in-person purchase__
______________________________________________________________________________________

6. Which of these features are numeric (or could be in a useful form)?
_Objective: Predict total number of customers who will use a certain discount coupon_
* __Percent value of the discount (e.g. 10% off, 20% off, etc.)__
* Size of the coupon (e.g. 4 cm2, 24 cm2, 48 cm2, etc.) 
_This is a difficult one -- yes the coupon code values are numeric but is the magnitude meaningful? Is a 48cm^2 coupon twice as valuable as a 24cm^2? It really depends on the context (banner ad, newspaper ad). Arguments could be made either way!_
* Font an advertisement is in (Arial, Times New Roman, etc.)
_These are categorical - not numeric, continue watching the video for a debrief_
* Color of coupon (red, black, blue, etc.)
_These are categorical - not numeric, continue watching the video for a debrief_
* Item category (1 for dairy, 2 for deli, 3 for canned goods, etc.)
_These are categorical - not numeric_
_______________________________________________________________________________________


