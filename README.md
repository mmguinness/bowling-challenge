
Bowling Challenge
=================

## My Process

* Fork Repo
* Setup Jest within project directory
* Install ESLint within project directory
* Start with idea for domain model 

![domain model](images/DomainModel.png)

* Aim to use a TDD approach to completing the project, as set out below:
   - Plan
   - Test
   - Implement
   - Refactor
   - Commit

* First test, frame 1, roll 1.
* Next, test for frame 1, roll 2.
* Next, test that total for Frame is calculated.

* Node Testing in Terminal:
    - node
    - > const Frame = require('./frame');
    - > const frame = new Frame;
    - > frame.firstRoll(4);
    - > frame.secondRoll(5);
    - > frame.frameTotal;
    - > 9
    - > frame
    - Frame { rollOne: 4, rollTwo: 5, frameTotal: 9 }

* Next, save frame score and reset rollOne & rollTwo for next frame.

* Next, save a strike if 10 pins knocked on rollOne.
* Node Testing in Terminal:
    - node
    - > const Frame = require('./frame');
    - > const frame = new Frame;
    - > frame
    - Frame {
    - rollOne: [],
    - rollTwo: [],
    - frameTotal: [],
    - frameBonus: [],
    - frameCounter: 0
    - }
    - > frame.firstRoll(10);
    - > frame
    - Frame {
    - rollOne: [ 10, 0 ],
    - rollTwo: [ 0, 0 ],
    - frameTotal: [ 10 ],
    - frameBonus: [ 'Strike' ],
    - frameCounter: 1
    - }
    - > 

* Next, save a spare if 10 pins are knocked over in rollOne and rollTwo.
* Node Testing in Terminal:
    - node
    - > const Frame = require('./frame');
    - > const frame = new Frame;
    - > frame
    - Frame {
    - rollOne: [],
    - rollTwo: [],
    - frameTotal: [],
    - frameBonus: [],
    - frameCounter: 0
    - }
    - > frame.firstRoll(4);
    - > frame.secondRoll(6);
    - > frame
    - Frame {
    - rollOne: [ 4, 0 ],
    - rollTwo: [ 6, 0 ],
    - frameTotal: [ 10 ],
    - frameBonus: [ 'Spare' ],
    - frameCounter: 1
    - }
    - > 

    * Next, caluclate bonus points for a spare and revise round total at the end of following frame.
    * Node Testing in Terminal:
        - node
        - > const Frame = require('./frame');
        - > const frame = new Frame;
        - > frame.firstRoll(4);
        - > frame.secondRoll(6);
        - > frame
        - Frame {
        - rollOne: [ 4, 0 ],
        - rollTwo: [ 6, 0 ],
        - frameTotal: [ 10 ],
        - frameBonus: [ 'Spare' ],
        - frameCounter: 1
        - }
        - > frame.firstRoll(2)
        - > frame.secondRoll(2)
        - > frame
        - Frame {
        - rollOne: [ 4, 2, 0 ],
        - rollTwo: [ 6, 2, 0 ],
        - frameTotal: [ 12, 4 ],
        - frameBonus: [ 'Spare', 0 ],
        - bonusPoints: [ 2 ],
        - frameCounter: 2
        - }


    * Next, caluclate bonus points for a single strike and revise round total at the end of following frame.

    * Next, caluclate bonus points for two strikes in a row and revise round totals at the end of following frames.

    * To do:
    - set up a `currentTotalPoints` to print at end of each frame
    - set up a full game of bowling conisting of 10 rounds
    - set up functionality for tenth frame conditions
    - Print full scoresheet at end of game
    - could use readline or similar to allow user input from CLI
    - noted, a lot of repetition in tests, need to refactor tests to group frames etc.
    - noted, a lot of repetition in frame class, need to refactor and consider pulling out a game class to reduce responsibility.


=================

## Project Brief

* Feel free to use google, your notes, books, etc. but work on your own
* If you refer to the solution of another coach or student, please put a link to that in your README
* If you have a partial solution, **still check in a partial solution**
* You must submit a pull request to this repo with your code by 9am Monday week

## The Task

**THIS IS NOT A BOWLING GAME, IT IS A BOWLING SCORECARD. DO NOT GENERATE RANDOM ROLLS. THE USER INPUTS THE ROLLS.**

Count and sum the scores of a bowling game for one player (in JavaScript).

A bowling game consists of 10 frames in which the player tries to knock down the 10 pins. In every frame the player can roll one or two times. The actual number depends on strikes and spares. The score of a frame is the number of knocked down pins plus bonuses for strikes and spares. After every frame the 10 pins are reset.

As usual please start by

* Forking this repo

* Finally submit a pull request before Monday week at 9am with your solution or partial solution.  However much or little amount of code you wrote please please please submit a pull request before Monday week at 9am. 

___STRONG HINT, IGNORE AT YOUR PERIL:___ Bowling is a deceptively complex game. Careful thought and thorough diagramming — both before and throughout — will save you literal hours of your life.

### Optional Extras

In any order you like:

* Create a nice interactive animated interface with jQuery.
* Set up [Travis CI](https://travis-ci.org) to run your tests.
* Add [ESLint](http://eslint.org/) to your codebase and make your code conform.

You might even want to start with ESLint early on in your work — to help you
learn Javascript conventions as you go along.

## Bowling — how does it work?

### Strikes

The player has a strike if he knocks down all 10 pins with the first roll in a frame. The frame ends immediately (since there are no pins left for a second roll). The bonus for that frame is the number of pins knocked down by the next two rolls. That would be the next frame, unless the player rolls another strike.

### Spares

The player has a spare if the knocks down all 10 pins with the two rolls of a frame. The bonus for that frame is the number of pins knocked down by the next roll (first roll of next frame).

### 10th frame

If the player rolls a strike or spare in the 10th frame they can roll the additional balls for the bonus. But they can never roll more than 3 balls in the 10th frame. The additional rolls only count for the bonus not for the regular frame count.

    10, 10, 10 in the 10th frame gives 30 points (10 points for the regular first strike and 20 points for the bonus).
    1, 9, 10 in the 10th frame gives 20 points (10 points for the regular spare and 10 points for the bonus).

### Gutter Game

A Gutter Game is when the player never hits a pin (20 zero scores).

### Perfect Game

A Perfect Game is when the player rolls 12 strikes (10 regular strikes and 2 strikes for the bonus in the 10th frame). The Perfect Game scores 300 points.

In the image below you can find some score examples.

More about ten pin bowling here: http://en.wikipedia.org/wiki/Ten-pin_bowling

![Ten Pin Score Example](images/example_ten_pin_scoring.png)

## Code Review

In code review we'll be hoping to see:

* All tests passing
* The code is elegant: every class has a clear responsibility, methods are short etc.

Reviewers will potentially be using this [code review rubric](docs/review.md).  Note that referring to this rubric in advance may make the challenge somewhat easier.  You should be the judge of how much challenge you want.
