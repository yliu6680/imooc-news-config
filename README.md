# City Connection Take Home Exercise

By [Paul Liu](mailto:paulliu6680@gmail.com)

## Instructions

1. Navigate to [repo](https://github.com/janephilipps/tic-tac-toe)
2. Clone locally using
   `git clone git@github.com:janephilipps/tic-tac-toe.git`
3. Install dependencies using `mvn install`
4. Run tests using `mvn test`
5. Go to the target, and start the appllication server using `java -jar ***.jar`
6. Navigate to app in [browser](http://localhost:8080)
7. Or import the maven project into IDE to run in the development environment.

## Environments

I mainly used Spring Boot 2, Java 8 to implement the challange.
I also utilized Spring Boot, Junit, Mockito to generate unit test and integration test for the application.
The project is built by Maven.

## Requirements

#### Build a two player tic tac toe app where a game is played by
#### alternating clicks until the game is won by X, O or is a tie.

I added a `message` that displays which player's turn it is based on the
number of turns taken. The `message` also displays whether a player has
won or if there is a tie.

#### Include a reset button so that when a game ends, the board can be
#### cleared and a new game can begin.

The reset button calls a method `_resetBoard()` which calls another
method `_getInitialState()` to reset the board.

## Bonuses!

#### Make the board fully responsive

I used the `vmin` unit of measure to make the `width`, `height`, and
`border` of the squares fully responsive.

#### Allow for more than 1 game to be played simultaneously

I have a state within the `App` that keeps track of the number of boards.
Because each board also has its own state, gameplay across multiple boards can
happen simultaneously without interference.
Back to top

Share this post on →   


12. Final steps before you hit send
Ok, now that you’ve written your README, you’re almost ready to hit send! Before you do that, take the time to double check all of your work using the following checklist:

Re-read the take-home challenge instructions to make sure you didn’t miss any requirements
Review your app’s code to ensure that it shines
Run your app’s automated tests and make sure they are all passing
Test your app manually and make sure everything is working properly
Test your app installation instructions from your README
Start an email draft and copy your README into it for convenience
If requested, make sure to attach a zip file of your code
Write an email to your contact at the company
Your email can be short and sweet - I always like to highlight something I enjoyed about the challenge or something I learned. Here’s an example:

Hi <NAME>,

I hope you had a great week! I had fun diving back into React with this
challenge. Here is my github repo and I've included my README below.
Please let me know if you have any questions.

Just so you know, I'm interviewing with a few other companies and I just
received an offer yesterday - I need to get back to them next week.
Of course, I am excited about the opportunity at <COMPANY NAME>, so I'm
looking forward to hearing from you!

Thanks,
<NAME>
