# CMPS 2200  Recitation 01

**Name (Team Member 1): **Jamie Hartman   
**Name (Team Member 2): **Charles Tyndal

In this recitation, we will investigate asymptotic complexity. Additionally, we will get familiar with the various technologies we'll use for collaborative coding.

To complete this recitation, follow the instructions in this document. Some of your answers will go in this file, and others will require you to edit `main.py`.


## Setup
- Make sure you have a Github account.
- Login to Github.
- Login to repl.it, using "sign in with github"
- Click on the assignment link sent through canvas and accept the assignment. 
- Click on your personal github repository for the assignment.
- Login in Repls https://replit.com/repls and then create a new replit by importing from github repository.
- You'll work with a partner to complete this recitation. To do so, we'll break you into Zoom rooms. You will be able to code together in the same `repl.it` instance. You can choose whose repl.it instance you will share. This person will click the "Share" button in their repl.it instance and email the lab partner.
- Make sure the dependencies are installed. Please use 'pip install -r requirements.txt'.

## Running and testing your code
- In the command-line window, run `./ipy` to launch an interactive IPython shell. This is an interactive shell to help run and debug your code. Any code you change in `main.py` will be reflected from this shell. So, you can modify a function in `main.py`, then test it here.
  + If it seems things don't refresh, try running `from main import *`
- You can exit the IPython prompt by either typing `exit` or pressing `ctrl-d`
- To run tests, from the command-line shell, you can run
  + `pytest main.py` will run all tests
  + `pytest main.py::test_one` will just run `test_one`
  + We recommend running one test at a time as you are debugging.

## Turning in your work

- Once complete, click on the "Version Control" icon in the left pane on repl.it.
- Enter a commit message in the "what did you change?" text box
- Click "commit and push." This will push your code to your github repository.
- Although you are working as a team, please have each team member submit the same code to their repository. One person can copy the code to their repl.it and submit it from there.

## Comparing search algorithms

We'll compare the running times of `linear_search` and `binary_search` empirically.

`Binary Search`: Search a sorted array by repeatedly dividing the search interval in half. Begin with an interval covering the whole array. If the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half. Otherwise, narrow it to the upper half. Repeatedly check until the value is found or the interval is empty.

- [ ] 1. In `main.py`, the implementation of `linear_search` is already complete. Your task is to implement `binary_search`. Implement a recursive solution using the helper function `_binary_search`. 

- [ ] 2. Test that your function is correct by calling from the command-line `pytest main.py::test_binary_search`

- [ ] 3. Write at least two additional test cases in `test_binary_search` and confirm they pass.

- [ ] 4. Describe the worst case input value of `key` for `linear_search`? for `binary_search`? 

The worst case for a linear search would be a key corresponding to a value at the end of the list.  This would make the runtime O(n) n being the length of the list.   

For binary search the worst case would be the key being in the first or last place as that would require the most amount of recursions to obtain the element.  This would end with a runtime of O(log n)

- [ ] 5. Describe the best case input value of `key` for         `linear_search`? for `binary_search`? 

The best case for a linear search would be a key corresponding to a value at the beggining of the list.  This would make the runtime O(1) as it only has to check the first value in the list.  

The Best case for a binary search would be the key corresponding to a value in the exact middle of the list (according to integer division).  In this scenario the runtime would be O(1) as it only has to do one pass to find the correct value. 


- [ ] 6. Complete the `time_search` function to compute the running time of a search function. Note that this is an example of a "higher order" function, since one of its parameters is another function.

- [ ] 7. Complete the `compare_search` function to compare the running times of linear search and binary search. Confirm the implementation by running `pytest main.py::test_compare_search`, which contains some simple checks.

- [ ] 8. Call `print_results(compare_search())` and paste the results here:

|            n |    linear |   binary |
|--------------|-----------|----------|
|       10.000 |    -0.005 |   -0.011 |
|      100.000 |    -0.017 |   -0.009 |
|     1000.000 |    -0.216 |   -0.049 |
|    10000.000 |    -2.200 |   -0.018 |
|   100000.000 |   -37.951 |   -0.040 |
|  1000000.000 |  -445.366 |   -0.030 |
| 10000000.000 | -3178.341 |   -0.037 |

- [ ] 9. The theoretical worst-case running time of linear search is $O(n)$ and binary search is $O(log_2(n))$. Do these theoretical running times match your empirical results? Why or why not?

These theoretical times do match with the empirical results. As the size of n increases exponentially so does the the runtime of the linear algorithm. This matches the O(n) runtime.  As the n increases exponentially, the binary search algorithm increases at a much lower rate (log n).

- [ ] 10. Binary search assumes the input list is already sorted. Assume it takes $\Theta(n^2)$ time to sort a list of length $n$. Suppose you know ahead of time that you will search the same list $k$ times.


  + What is worst-case complexity of searching a list of $n$ elements $k$ times using linear search?


  The worst-case complexity of searching a list of n elements k times using linear search would be O(k * n) as the worst case scenario for searching linearly is O(n) and you are doing it k times.


  + For binary search?


    The worst-case complexity of searching a list of n elements k times using binary search would be O(K * log n) as the worst case for searching using binary search is O(log n) and you are doing it k times.
  

  + For what values of $k$ is it more efficient to first sort and then use binary search versus just using linear search without sorting?


  If you are searching more than one time (k > 1) you should go with sorting and then using binary sort.  If the list is already sorted you should always go with binary search  If you are only searching the list one time and it is unsorted, then you should linear search.
