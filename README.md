# Event Planning App

Note: The openWeather API keys are not committed to the repository. Therefore the app will not work out of the box. If you wish to test the application, you will need to get your own API key from openWeather and add it to your own '.env.' file. 


## Introduction
This was completed as an assignment for the course Web Development II. 

In this assignment, you will demonstrate your ability to combined front-end-and-back-end app, using the skills from all three units, including AJAX.

## Details

We're planning an event. At this level, it's not quite going to be complete, but it's a start.  Users can look at a list of days, with information about what other users have voted, and place their own votes on what days are good for them, or bad for them, or whatever.

We'll assume all users of the site are interested in the same event.

* View existing votes
    * Implement a function that makes an AJAX request to the backend for the existing votes, for the relevant dates
        * I suggest calculating the date and sending some `minDate` and `maxDate`, or `minDate` and `dateCount`, or something like that
    * You must also implement a backend route that will give this information
        * again, I think it's sufficient to call `db.getVotesForDate(date)` in a loop and put those in an array
    * When the frontend receives the response, read the response, and if it was successful, make appropriate calls to `updateOthers()`
    * As with signup/login/logout, on success respond with 200 and suitable JSON data, and on failure return non-200 and an optional error JSON

* Signup, Login, Logout
    * Using vanilla JavaScript to attach event handlers to the signup/login functionality in the header
        * When the user clicks a button, send an appropriate AJAX request to the backend
        * Also process the AJAX response; if the signup/login/logout was successful, update the header
    
    * You must also implement the backend routes
        * there should be no need to write your own DB code; the methods I have provided should be sufficient
        * the backend routes should
            * if the request was successful, return status 200, and a JSON object with relevant session data (but not the password)
            * if the request was bad (e.g. bad password, e.g. duplicate user), an error status, and optionally also a JSON object with error information of some kind
            * of course you must set cookies so that if the user refreshes the page, they stay logged-in or logged-out or whatever

* Weather via 3rd-party API
    * We'll use https://openweathermap.org/api/one-call-api to get weather data.
        * I have no previous experience, but it seemed pretty great
        * You need to **SIGN UP FOR AN ACCOUNT TO GET AN API KEY**
            * I have tuned the assignment to be easy on the Free tier
            * I did not give them any credit card data etc, you don't need to either
    * You must make an API call from the front-end, with AJAX, to get the weather for the 7 days covered by your event plan
        * you need to give them a lat and long.  I put the BCIT lat/long in the `.env` file, you can change that if you really wanna
    * For each day, choose a suitable temperature to use, and a summary of the weather, and an icon
        * and update all of the cards appropriately
    * Try to keep your API key secure
        * This means you'll need to make a VERY OBVIOUS PLACE for me to put my API key in to test your app
        * Oh, hey, I already made it for you, it's a `.env` file
        * So use the `.env` file


In an effort to bring down the time required for this Assignment, I have
* completed the assignment (all of PASS, and most of SATISFACTORY)
* deleted all the AJAX calls
* deleted all the backend calls that directly reply to AJAX calls (several routes, over 50 lines)

Soooo, you should be able to just write AJAX, I guess?  Though, I'll note that while *many* of the deleted sections were quite short (a few lines), some were not short (up to 20 lines).

You don't HAVE to do it this way.  This is just my best effort to make it as straightforward as possible.



* My own voting
    * Make the voting buttons actually work
        * Add event handlers and AJAX calls to Yes/??/No to vote
        * Also add backend routes
        * The ?? button cancels my previous vote for this date
        * If you've already voted, you can change your vote at any time

    * Appearance
        * I **should not see** my own votes in the list of others' votes below the voting buttons
            * hint: getting this 100% correct may require attention to the login/logout flow
        * If I have not voted (or voted and then unvoted), all three buttons should have default opacity and default borders
        * If I have voted for Yes or No, then that button should get a thicker border, and the other two buttons should become 50% opaque
        
* Add a refresh button
    * so that you can manually trigger the AJAX call to the backend to update what the votes are


