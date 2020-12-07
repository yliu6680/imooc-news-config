# City Connection Take Home Exercise

By [Paul Liu](mailto:paulliu6680@gmail.com)

## Instructions

1. Navigate to [repo](https://github.com/janephilipps/tic-tac-toe)
2. Clone locally using
   `git clone git@github.com:janephilipps/tic-tac-toe.git`
3. Install dependencies using `mvn install`
4. Run tests using `mvn test`
5. Go to the target, and start the appllication server using `java -jar ***.jar`
6. Open browser or to other test tools, and navigate to [(http://localhost:8080](http://localhost:8080)
7. Or import the maven project into IDE to run in the development environment.

## Environments

The challenge is implemented by Spring Boot 2, Java 8. I also utilized Spring Boot, Junit, Mockito to generate unit test and integration test for the application. The project is built by Maven.

## Basic Requirements

#### Build a Spring Boot application that could read cities data from file (.txt file).

I added this functionality in the Spring Boot application with life cycle method, so the data will be only loaded one time when the application is initializing. And the data will be interpreted into a non-directed graph. I utilized hash map and hash set to store the map as adjacent lists.

#### Implemented Breath First Search (BFS) algorithem to search the possible roads between two different input cities.

I utilized BFS to search whether the two cities are connected in the graph from the adjacent list, more details could be found in the analysis section.

#### Built controller to let user utilize GET request and URL parameter to perform the search.

I constructed RESTful API to let users to call the related controllers and service.

#### Created tests

I created more than 20 unit tests and integration tests for the application, covered nearly all classes and methods I created.

## Other Bonus

#### Add a cache to improve the performance

I added a cache layer for the application. So once the application is started, every valid query and result of the cities connection will be stored into a cache. I implemented the cache with Java Collection framework, and the cache is a LRU cache. 


## Demonstration Of The Application

The whole cities data in the application is listed below:
```
Boston, New York
Philadelphia, Newark
Newark, Boston
Trenton, Albany
Los Angeles, Irvine
Seattle, Los Angeles
Houston, Boston
Chicago, San Fransisco
San Antonio, Chicago
Dallas, Chicago
```

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
