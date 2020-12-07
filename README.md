# City Connection Take Home Exercise

By [Paul Liu](mailto:paulliu6680@gmail.com)

## Instructions

1. Navigate to [repo](https://github.com/janephilipps/tic-tac-toe)
2. Clone locally using
   `git clone git@github.com:janephilipps/tic-tac-toe.git`
3. Install dependencies using `mvn install`
4. Run tests using `mvn test`
5. Go to the target, and start the application server using `java -jar ***.jar`
6. Open browser or to other test tools, and navigate to [(http://localhost:8080](http://localhost:8080)
7. Or import the maven project into IDE to run in the development environment.

## Environments

The challenge is implemented by Spring Boot 2, Java 8. I also utilized Spring Boot, Junit, Mockito to generate unit test and integration test for the application. The project is built by Maven.

## Basic Requirements

#### Build a Spring Boot application that could read cities data from file (.txt file).

I added this functionality in the Spring Boot application with life cycle method, so the data will be only loaded one time when the application is initializing. And the data will be interpreted into a non-directed graph. I utilized hash map and hash set to store the map as adjacent lists.

The city.txt file is stored in the resources folder of the maven project, users could replace the txt file with their own.

#### Implemented Breath First Search (BFS) algorithm to search the possible roads between two different input cities.

I utilized BFS to search whether the two cities are connected in the graph from the adjacent list, more details could be found in the analysis section.

#### Built controller to let user utilize GET request and URL parameter to perform the search.

I constructed RESTful API to let users to call the related controllers and service. I have added validation steps in controller and service layer, so if the input parameter is not valid, the application will return No connections.

#### Created tests

I created more than 20 unit tests and integration tests for the application, covered nearly all classes and methods of the controller, service, and utils code.

## Other Bonus

#### Add a cache to improve the performance

I added a cache layer for the application. So once the application is started, every valid query and result of the cities connection will be stored into a cache. I implemented the cache with LinkedHashMap in Java Collection framework, and the cache is a LRU cache. 

## Demonstration Of The Application

The whole cities data in the city.txt file is listed below:
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

The application could be called by using the follow URL pattern, http://localhost:8080?origin={city1}&destination={city2}.

#### Normal test cases
Basic test cases between Boston and Newark, Boston and Philadelphia, Philadelphia and Trenton, and non existed cities are shown below.

![image](https://github.com/yliu6680/imooc-news-config/blob/master/Boston_Newark.png)

![image](https://github.com/yliu6680/imooc-news-config/blob/master/Bos_Phi.png)

![image](https://github.com/yliu6680/imooc-news-config/blob/master/Phi_Alb.png)

![image](https://github.com/yliu6680/imooc-news-config/blob/master/Non_Exi.png)

#### Invalid test cases
Invalid test cases, including invalid input, empty parameter, and null parameter are shown below.

![image](https://github.com/yliu6680/imooc-news-config/blob/master/Invalid_Name.png)

![image](https://github.com/yliu6680/imooc-news-config/blob/master/Empty_Name.png)

![image](https://github.com/yliu6680/imooc-news-config/blob/master/Null_Input.png)

## Anlysis And Implementations

#### Implementation of Interpreting Data To Graph



#### Implementation Of The Searching Algorithm

I implemented the algorithm by Breath First Search, it's an algorithm first expand all neighbour nodes of the origin node, and then go deeper of the graph.

The data structure I used for my algorithm is queue, and implemneted by Java LinkedList. I also used hashset to record all visited node, in case there are any loops in the graph. The stops could be describe as follow:

   1. Add the origin city name in the queue.
   2. Poll the queue, and get a city name. 
   3. Find the city name in the heads of all adjacent lists, all heads are the keys of the hashmap. 
   4. Find the adjacent list for the head.
   5. Iterate the hashset. If we find the destination city name in the hashset, then we are done. 
   6. Otherwise, if the city name is not in the visited set, then add the city name in to the queue and visited hashset.
   7. Repeat the algorithm from step.2 - step.6, until the queue is empty or we find the final result.
   8. If we still not find the result, then the two cities are not connected.

#### Implementation Of The Cache

I implemented the Least Recently Used cache with LinkedHashMap. The operations for the cache is shown below:
   
   1. Initilize the LRU cache with a capacity.
   2. Get item from the HashMap, if it exists, then we need to swap the item with the last node in the LinkedList of the LinkedHashMap.
   3. Put item in the HashMap, if the capacity has already fulled, then remove the first node in the LinkedList of LinkedHashMap.

So each time the recently used item will be updated to the last node in the LinkedList, and will be kept for longer time. The item will be replaced based on the last time it is used by the user. 

#### Analysis Of The Algorithm

Assumes there are N lines in the city.txt file, M city names are in the file, and the capacity of the cache is C. And hashmap and hashset will work perfectly, so each operation ill only cost O(1).

The

The BFS:

The BFS algorithm will

#### Parameters validation

Parameter vlidations are added in the controller layer and the service layer, so we could get No Connection response when user's request parameters are not valid.

#### Tests 

I wrote unit test cases for the graph search algorithm, and also test it in the service layer and controller layer with stubs, mockito, and MockMvc. I also utilized Spring Boot to generate integration test for the whole RESTful API. 

#### Extensible Interfaces

I created CityDataReader interface and CityDataCache interface, and implements them with Java IO and LRU cache in this application. It could be easy to add more implementation based on the interfaces to get the cities data from database, cloud storage, and cache from other cache like LFU cache, or database Redis or cloud cache.


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
