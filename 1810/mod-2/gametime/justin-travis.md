# Game Time
* Students: Justin & Travis
* Evaluator: Brittany


### Functional Expectations

* 4 - Application is fully playable and exceeds the expectations set by instructors

* Still some bugginess around the wagering for final jeopardy -- it seems like the wager is adding onto everybody's wager when you click through those numbers rather than resetting each time. 
* +1 for deployment to GH pages

### User Interface

* 2 - The application has many strong pages/interactions, but a few holes in areas that are important for determining what the user should be doing and where they should be looking.


* Font is a bit difficult to read in places; save cool/unique fonts for headings and large titles, not smaller text like on inputs and buttons
* Is the loading bar actually doing/caculating progress on something? Or is it just there for show? It looks kind of out of place right now/inconsistent with the overall UI.
* Name entry page is way too spread out, looks like it was designed for a mobile device even when being viewed on a smaller laptop. 
* Difficult to tell whose turn it is with the small font text in the bottom left.
* Hover effects are too subtle/non-existant which makes it difficult to tell what's actually clickable or not
* I think it's a bit *more* confusing to have the players rotating at the top to denote the current player -- you want to avoid moving UI elements around on people unless absolutely necessary. With the rotation as it is, now as a player, I have to keep looking in a different spot to find my score.
* Shouldn't be able to start a game without inserting player names -- it makes the text in the bottom left unusable.
* Not sure what the negative numbers are when the wager option pops up for daily doubles -- I would simplify this to just have a single number input field where they can enter their wager manually rather than clicking those numbers. It's also difficult to know that I'm supposed to click on the final wager in order to move on to the actual question. This should be a clearer button that says something like 'Submit Wager >'


### Testing

* 2 - Project has sporadic use of tests at multiple levels. The application contains numerous holes in testing and/or many features are untested.

* These two tests  [1](https://github.com/JustinD85/jeopardy/blob/master/test/wager-test.js#L25-L28) and [2](https://github.com/JustinD85/jeopardy/blob/master/test/wager-test.js#L40-L43) are redundant. Just stick with 2.

* Player class is missing tests for incrementing/decrementing wagers and scores.

* Clue class is missing tests for verifying if the answer is correct or not.

* [None of this needs to be tested](https://github.com/JustinD85/jeopardy/blob/master/test/index-test.js) and doesn't give your application any additional integrity



### JavaScript Style & OOP


* 3 - Application is thoughtfully put together with some duplication and no major bugs. Developer can speak to choices made in the code and knows what every line of code is doing. Application is organized into classes (and correctly uses inheritance) with some misplaced logic and no major bugs. Business-logic code is mostly separated from view-related code. Developer can speak to choices made in the code and knows what each line of code is doing.

* Wierd to me that you'd be setting an instance property of value in [this method](https://github.com/JustinD85/jeopardy/blob/master/js/wager.js#L6-L8) that's not defined in the constructor anywhere. I would just reassign the `pointValue` property instead of creating another property.

* As discussed in eval, the whole data manager class is a bit convoluted -- manipulate your data wherever you need it, into whatever format you need it in rather than in this hidden file. It's a bit too much of an abstraction and I'd rather just see the `clues` array on your Game class be your source of truth.

* [Checking answer](https://github.com/JustinD85/jeopardy/blob/master/js/game.js#L12) should belong to the clue class, not the game class. Updating the wagers and player scores should all be moved into the player class as well out of the game class. (e.g. a player is the only thing that knows about it's score, and that score is unique to that player, so that player should be the only thing in your codebase that can manipulate that value.)

* [Value](https://github.com/JustinD85/jeopardy/blob/master/js/clue.js#L6) can sometimes be a reserved keyword (notice the syntax highlighting is different here). Just keep the property called `pointValue`. No need to change it.

* [These](https://github.com/JustinD85/jeopardy/blob/master/js/clue.js#L7-L8) two instance properties are a little redundant. You don't usually want to store "derived data" anywhere. e.g. if you have the category ID stored, you can always find and reference the category name later in your codebase by leveraging that id value.

* Don't leave [unused code](https://github.com/JustinD85/jeopardy/blob/master/js/board.js) in your codebase. It's confusing for new developers to jump into.


### Workflow

* 4 - The developer/team effectively uses Git branches and many small, atomic commits that document the evolution of their application with descriptive commit messages. The team displays good pairing practices (driver-navigator, dividing up work, etc) and utilizes some sort of planning tool (GitHub issues, Waffle, Trello, etc). The team develops a clear MVP (minimum viable product) and conducts a DTR (define the relationship). Both members contribute meaningfully to the application.

* Mostly nice, consistent commit messages except for little ones like [this]
(https://github.com/JustinD85/jeopardy/commit/725acca9844a940e4452a1cec58dbda4f02d4be9) that snuck in.
* Nice use of issue numbers to auto-close them as you push
* You might want to look into `git squash` to merge some commits before you push them into master -- just a nice tool to be aware of. You can reduce duplicate commits (I noticed a couple) that do the same thing like 'Update README' (if you do this 5 times you can just squash it into a single commit when you're done that includes all the changes you made over all those commits)