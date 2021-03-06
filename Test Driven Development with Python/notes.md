# Obey the Testing Goat
- This book require Django 1.something but I'll use Django 2 to match what we have at work.

# Chapter 1: Getting Django Set up Using a Functional Test
- We should always start to code with a test (it's like kungfu it requires a discipline)
- We should furthermore start with a FAILING test and make it work.

# Chapter 2: Extending Our Functional Test Using the unittest Module
- functional test == acceptance test == ende to end test
- The functional tests need to be readable by human so we should put comments in place so that we know what is hapenning.
- We can use the unittest module to simplify most of our testing with redundant task instead of always using raw assert call
- unittest is a class based framework with function we need to define.
- watch out if we have setup, it doesn't exist we need to use setUp instead
- A user story is really important in this case
- Separating your projects into app is crucial to not have a mess, for API however it might be a different story. Will have to double check what I could do for that. However, if we have services (not micro yet) we could have each of them have their own version of the code! For instance /onboarding/v1/whatever instead of /v1/onboarding/whatever. this will make each service more independant.

# Chapter 3: Testing a Simple Home Page with Unit Tests
- Functional test is testing the code from the outside (blackbox) and unit test is to test the code from the inside. What will follow is a solid plan we might want to follow:
- We start by writing a functional test, describing the new functionality from the user’s point of view.

- Once we have a functional test that fails, we start to think about how to write code that can get it to pass (or at least to get past its current failure). We now use one or more unit tests to define how we want our code to behave—​the idea is that each line of production code we write should be tested by (at least) one of our unit tests.

- Once we have a failing unit test, we write the smallest amount of application code we can, just enough to get the unit test to pass. We may iterate between steps 2 and 3 a few times, until we think the functional test will get a little further.

- Now we can rerun our functional tests and see if they pass, or get a little further. That may prompt us to write some new unit tests, and some new code, and so on.

- The more nervous we are about getting our code right, the smaller and more minimal we make each code change—​the idea is to be absolutely sure that each bit of code is justified by a test.

# Chapter 4: What Are We Doing with All These Tests? (And, Refactoring)
- Refactoring is super important and Django test client is a good tool to use for making the tests more concise. Should take a deeper look at it at some point.
- Should start new project not directly with a API, but instead follow the gentle refactoring we have been doing at GRAD4. This will allow us to move a bit faster when starting new project with Django.

# Chapter 5: Saving User Input: Testing the Database
- The point of TDD is to allow you to do one thing at a time, when you need to. At any given moment only do what is necessary to get the functional tests one step further.
- Just learned about f string in python where you can use them to get the same behavior as a sprintf in C.
- Helper functions in the tests classes should be used to reduce the complexity just like in non-test code.
- Similarly if a unit test is getting longer and longer, it should be broken down into sub component to test
- Should keep the test clean and descriptive so that they are easy to debug / maintains

# Chapter 6: Improving Functional Tests: Ensuring Isolation and Removing Voodoo Sleeps
- Django LiveServerTest is support important to do the functional tests
- Different tests shouldn’t affect one another. This means we need to reset any permanent state at the end of each test. Django’s test runner helps us do this by creating a test database, which it wipes clean in between each test.
- Selenium implicit wait seems to suck, using polling is a bit better

# Chapter 7: Working Incrementally
- TDD is very against big design up front (MVP)
- YAGNI! You Ain't Gonna Need It!
- in a test having one '#' means that it's a user story and having '##' means that it's a metacomment
- TDD makes us realize how much things can mess up, because usually as soon as we do some amount of change we have a bunch of tests firing up.
- Red/Green/Refactor should be printed out somewhere in the office
- Working from vanilla django with super ugly frontend with all the functionalities we need is actually a pretty solid way of getting an MVP, will keep that in mind for the next time we need to have something off the ground fast.
- we can capture a parameters in the url using <int:id> for instance
- When we want to create something new we don't put a trailing / at the end of the url for instance /list/new
- f string are quite usueful, they are like sprintf in C
- Remember that all tests need to start with the keyword test_* in django

* At Testing the Response Context Objects Directly Now
