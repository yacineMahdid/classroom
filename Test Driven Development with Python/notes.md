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