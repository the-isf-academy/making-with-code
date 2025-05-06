---
title: 3.B.0 Databases and Models
draft: True
---

# Databases and Models

When looking at databases for the first time, one may think a database is just a fancy spreadsheet. In a spreadsheet, there is a screen full of little rectangles, and in these rectangles, we can enter and store data. When we look at a database using a database viewer, it can look very similar to a spreadsheet.

Here's an example of MS Access (database) and MS Excel (spreadsheet).


MS Access (Database) | MS Excel (Spreadsheet)
---------------------|-----------------------
<img src="/images/courses/cs10/unit02/ms_access.jpg" width="400"> | <img src="/images/courses/cs10/unit02/ms_excel.png" width="400">
Can you spot the differences?

Even though databases and spreadsheets may look similar, they actually are very different. What are these differences?

Here's an example:

Say we want to keep track of the food that we ate in a spreadsheet. We enter the type of food we ate in a column and its portion size in another column. Say we ate a banana. We keep track of the banana and type "Banana" in the first column and "one banana" as a portion in the second column. Then in another meal, we ate rice and we type "250g". Then in another meal, we ate grapes, and we type 5 (as in the number 5). Our data will look something like this in a spreadsheet.

<img src="/images/courses/cs10/unit02/food_eaten_data.png" width="300">

Say we are really looking at being healthier and we collect our eating data for a month. We would store all of our data in our spreadsheet just like what we have in the image. Awesome!

Now, we want to create a program that can figure out the calorie count of what we ate during that month. Have some category breakdowns... and a nice dashboard...

**Houston, we have a problem!**

Do you know what the problem is? *Hint: Look at the data...*

If you look at the data in the ***Portion*** column, we have both strings and integers. In addition to this, we have to figure out what the strings and numbers are and what they represent.

This situation that we have here is very difficult to deal with programmatically. In fact, unless we create our program to handle each food individually, and then deal with every variation of food portion typed out for that food ("5 grapes", 250 (grams of grapes, as in the integer), "ate grapes until I puked", etc), we won't be able to get an accurate picture from our data and our app will fail.

So what can we do about this? Enter Models and Business Logic.

## [A] Databases, Models, Business Logic and their Importance

In this example, the calorie count idea was decided on after the fact and because of this we never thought about how data was collected. Our collected data ended up to be pretty difficult to use programmatically. However, if we had some foresight on our data design before we start coding, the data entered into our database wouldn't be like in our example. The data in ***Portion*** will be **clean and useable** unlike what it is now.

If only we can find a person that can make sure that this doesn't happen... That's right! There's the Software Architect!

This is where we as a Software Architect are so important. The Software Architect is the person making important decisions about the app's data (and the important bits and bobs of the app). For our app, Software Architects define what the data is and create *Models* and *Business Logic* before the actual coding.

### [Models]

A *database model* is defined as the logical design and structure of a database and defines how data will be stored, accessed and updated in a database management system.

So the Software Architect designs good database models and uses them so that data, like the data in ***Portions***, will be a specific type of data when it's entered into the database. That way our data is clean and we don't need to code our app to handle an **infinite number of use cases**. Hooray!

{{< checkpoint >}}
For the calorie counting app in our example, what do you think the type of values in ***Portion*** should be? Create a table in a spreadsheet that has good data, unlike the situation that we have now.
{{</checkpoint >}}

If you guessed integer values, you are correct! Integers would be more appropriate than strings here as numbers can be more easily quantifiable. We can also use integers in mathematical calculations. (How do we quantify and calculate "Ate so much of X that I puked"!?!?)

Ok, we decided that the data will be an integer value. Great! But we need to be careful with this decision as numbers need to be differentiated too. There's still a difference between 1 as a whole apple, 1 as a portion of apples and 1 as in one gram of apple even though they all are represented by the number one. So how do we do this?

### [Business Logic]

Now, we use some Business Logic (or sets of business rules) and decide what our data really is. We need to decide what the number in the ***Portion*** column represents because, like in the example, 1 can mean a lot of things.

Once we make a decision to the Business Logic, we need to make sure it's consistent throughout the app. Let's say our Business Logic determined that the number in ***Portion*** is "grams" (1 meaning 1g of apple), our frontend cannot display the number 1 as "one apple" or "1 portion or apple". Similarly, we shouldn't expect the app to handle a user entering 1 into the database (thinking it's a portion of apples) and suddenly our app magically knows the user really meant 1 "portion of apples" when in fact it's 1 gram. If this happens, we're back at the same problem as before where we need to deal with all possible combinations of data entry. YUCK!

So Software Architects design Business Logic along with models and databases to make sure that data has meaning and flows consistently throughout the app.

{{< checkpoint >}}
Now add a label to your table to describe the what the data should be in the **Portion** field in your table.
{{< /checkpoint >}}

### [Conclusion]

Before we actually code our app, we want to design our data so that we don't have to code for 1000+ use cases. We also don't want to fix any data related errors half way into our development cycles because the someone says they want to change our data and business logic half way into our development.

As a Software Architect, we decide on what type of data the data is, and decide the Business Logic associated with that the data. And these decisions don't change in the middle of our development cycle because if these decisions are changed, then code will need to change, and that's a waste of time and money.

The mantra for Software Architects to member would be: **Why fix bugs when we can design these problems away!**

You see the importance of the Software Architect? Software Architects are paid to think and come up with designs that are infallible **first**. They think of solutions that, not only are great designs, but also save time and money during the development cycle.

![Gorilla getting Code Monkey's bananas](/images/courses/cs10/unit02/Codemonkey.png)

{{< checkpoint >}}
Now that we have read about databases and models, how will you take this learning and apply it to your own web app?
{{</checkpoint >}}

I hope this introduction has given some insight into databases, models, business logic and also how important this role is. In the next mini-lesson, we will look at how we use models with Django and real code.
