# TRZ (The Resident Zombie) - Frontend

## Problem Description

The world, as we know it, has fallen into an apocalyptic scenario. The "Influenzer T-Virus" (a.k.a. Twiter Virus) is transforming human beings into stupid beasts (a.k.a. Zombies), hungry to cancel humans and eat their limbs.

You, the last survivor who knows how to code, will help the resistance by deploying a system to connect the remaining humans. This system will be essential to detect new infections and share resources between the members.

## Requirements

You will develop a website that consumes a ***REST API***, which will store information about the survivors, as well as the resources they own.

The system must fulfill the following use cases, sorted by importance, to guarantee the survival of the resistance.

- **Add survivors to the database**:

  A survivor must have a *name*, *age*, *gender*, *last location (latitude, longitude)* and *inventory*.

  The survivor inventory can have: **Fiji water**, **Campbell soup**, **first aid pouch**, and **AK47**.

  The interface has to have a list of those items for the user to add to the inventory. The user must also be able to see a map to assign the last location (initially with the current position of the survivor). An intuitive and practical interface ensures the security of the members of your group.

  There is a bonus point if you implement another security measure. Some stupid higher up thinks that we have a spy in the group. So you will record a false position. Whenever the latitude and longitude position you get from the map, register it as 10 km North. So if the database leaks to the spy, the known member positions won't be compromised.

- **Update survivor location**:

  Survivors must have the ability to update their last location. When added to the database, a survivor will receive a unique identification from the system (implemented as a Surrogate Key. Research it). The survivors must be able to search for themselves and effectively update the last location using that identification.

- **Flag survivor as infected**:

  In a chaotic situation like that, a survivor may inevitably get contaminated by the virus.  When this happens, we need to flag the survivor as infected.

  An infected survivor cannot trade with others, can't access/manipulate their inventory, nor be listed in the reports (infected people are kinda dead anyway, see the item on reports below). So sad when people fall for the Influenzer T-Virus.

  **A survivor is marked as infected when at least five other survivors concur and report their contamination.**

  When a survivor is infected, they lose their inventory to that last person to mark them (the 5th person). Yeah, life is harsh like that. The server-side API will take care of that.

  For practical purposes, it's expected to be possible to search for a survivor by name to flag that survivor as infected. Who's gonna remember the identification from the whole group with the life at risk?

- **Survivors cannot Add/Remove items from inventory**:

  A new user must register their belongings alongside the sign-up process. After that, they can only change their catalog through trading with other survivors. Make sure that an error in the system doesn't end up with corrupted data!

  The items allowed in the inventory are described above in the first feature.

- **Trade items**:

  Survivors can trade items among themselves.

  To do that, they must respect the price table below, where the value of an item is described in terms of points.

  Both sides of the trade should offer the same amount of points. For example, 5 Fiji water and 5 first aid pouch (5 x 14 + 5 x 10) are worth 6 AK47 (6 x 8) plus 6 Cambell Soups (6 x 12) - and yes, you will die without water for a day. You'll also die if you have a severe untreated wound. That's why those items are more expensive than weapons and food!

  The trades won't be stored by the API, but the items will be transferred from one survivor to the other.

| Item              | Points   |
|-------------------|----------|
| 1 Fiji Water      | 14 points |
| 1 Campbell Soup   | 12 points |
| 1 First Aid Pouch | 10 points |
| 1 AK47            |  8 point  |

  As a tip, it's probably good to start the application with a reasonable amount of goods in stock, so it's easier to match prices and quantities for trading.
  
  The clever among you must have realized by now that someone can trade all their items for a weapon, kill everybody, and take all the food later. Yeah, that can happen. Bonus points if you have a clever solution for this conundrum.


- **Reports**

  The interface must show the following reports, served by the API:

    1. Percentage of infected survivors.
    1. Percentage of non-infected survivors.
    3. The average amount of each kind of resource by the survivor (e.g. 10 Fiji Waters per survivor)
    4. Points lost because of the infected survivor.

---------------------------------------

## REST API

To communicate with the server, you'll have available the endpoints documented in this swagger: http://zssn-backend-example.herokuapp.com/swagger-api/index.html

## Notes:

1. You can use **any** JavaScript _framework_/lib of your preference if needed - but you must use one, because most real world projects will have some framework in place;
2. You can use an ES6 or CoffeeScript _transpiler_ if you prefer;
3. You can use CSS _precompilers_, like SASS, PostCSS, Less or Stylus, again, if you prefer; But you will have a better evaluation if we can see that you can properly design custom CSS.
4. A pretty design is nice to have, but minimal UX is more important. Your life is in risk; it's not good to have a system that is hard to use;
5. New _features_ are welcome, but the priority is the previously listed _features_, sorted by importance;
6. The survivor should not reenter data in case there's some network problem. Practicality and objectivity are ideal.
7. Just to be clear: tests (unit, acceptance) are obligatory. We won't even look code without tests.

This test must be done in one week or less. If you take MORE than one week, we won't even try evaluating. A "senior" is able to do this in just a few hours, or less.

**Important:** For the evaluation, keep this in mind: you don't need to complete every single feature listed in this test (consuming every single API in the documentation). For example, you can implement just the Survivor CRUD interface. But the fewer features you achieve, the more you have to nail what you deliver. So, if you deliver just one feature, we expect it to be a perfect implementation (structure, organization, testing, style, overall quality, fanciness, etc.). The more features you deliver, the fewer details you have to add. It's your choice.

## Sharing your solution

After finishing your implementation, DO NOT push your code to GitHub, GitLab or any other publicly available repository. You will zip the project folder (including the .git directory) and send the zip file to the person interviewing you.


**ARE YOU LOGAN PAUL??**
