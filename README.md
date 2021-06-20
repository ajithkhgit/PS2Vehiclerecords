# PS2Vehiclerecords

Problem Statement
A warehouse has certain number of trucks that transport supplies in and out of the warehouse. Each
truck has a unique identifier and a counter to keep a track of how many orders did each truck fulfilled.
Whenever a truck moves in/out of the warehouse its unique ID is recorded.
Every day when the truck arrives at the warehouse for the first time, the counter is set to 0. From then
onwards, the counter is incremented each time the truck enters and exits the warehouse.
When the truck will leave the warehouse to deliver supplies to the client, an order will be opened
against its ID in the system and the counter will be ‘odd’. This is considered as an open order. The
order will be marked as closed when the truck arrives back at the warehouse and the truck’s counter
will be ‘even’ at that time. If the counter is 0, it means they have not started working and have just
arrived to the warehouse for the first time in the day. Hence the counter indicates the number and
status of orders.
The warehouse manager requires your assistance in keeping a track of open and closed orders
through an automated system.
In addition to this each truck can do a maximum of ‘x’ deliveries in a day. The implemented system
will also help the manager in assigning orders to each vehicle. It can identify which trucks have
completed their maximum deliveries for the day and which ones can still be assigned with more orders.
The warehouse manager uses the above system to answer the below questions:
1. Total vehicles that came to the warehouse for work?
2. Check specific truck whereabouts
3. Number of open, closed and yet to be fulfilled orders
4. List of trucks that have moved in/out of the warehouse more than ’z’ number of times.
5. List and number of trucks that have completed their maximum deliveries for the day
6. List and number of trucks that are currently in the warehouse and available to deliver suppliesRequirements:
1. Implement the above problem statement in Python 3.7 using BINARY TREE ADT.
2. Perform an analysis for the questions above and give the running time in terms of
input size: n.
The basic structure of the drug node will be:
Class TruckNode:
def __init__(self, Uid):
self.UId = Uid
self.chkoutCtr = 0
Operations:
1. def _readTruckRec(self, tNode, Uid): This function reads vehicle ids entering and leaving
the warehouse from the inputPS2.txt file. One ID should be populated per line (in the input
text file) indicating entry or exit separated by comma. Input data is used to populate the tree.
When truck arrives at the warehouse for the first time, the counter is set to 0. If a truck record
is already added to the tree, then the counter is incremented for every subsequent occurrence
of that truck in the input file.
If the counter is odd, it means that the truck exited the warehouse and there is an open order
against that truck ID in the system. On the other hand, if the counter is even the truck has
arrived back to the warehouse and the order is closed.
The first line indicates maximum deliveries a vehicle can do. Vehicle entry starts from the
second line. If vehicle deliveries exceed the maximum allowed deliveries, then display a
message ‘vehicle id xx no longer available for service’ and skip that entry.
Use a trigger function to call this recursive function from the root node. Sample Input
2
34
453
56
34
643
231
31
31
453
34
34
342. def _updateTruckRec(self, tNode, Uid): This function updates the existing system with IDs
entering and leaving the warehouse from the promptsPS2.txt file. If the truck arrives at the
warehouse for the first time, the counter is set to 0. If the vehicle is already added to the tree,
then the counter is incremented to update occurrence of that vehicle in the input file. If the
counter is odd, it means that the truck exited the warehouse and if the counter is even the
truck arrived back to the warehouse. Each exit marks an open order while each entry except
the first indicates a closed order.
updateTruckRec: 112
updateTruckRec: 453
3. def _printTruckRec(self, tNode): The input should be read from the promptsPS2.txt file
with the tag as shown below.
printTruckRec
This function counts the total number of vehicles that came to the warehouse for work and
prints the list of vehicle ids added into the system and their counter separated by a ‘,’ in
outputPS2.txt. ‘0’ counter indicates the vehicle arrived at the warehouse for the first time and
has not started fulfilling any orders yet. The output file should show:
Total number of vehicles entered in the warehouse: xx
31, 1
34, 4
56, 0
231, 0
453, 1
643, 0
Use a traversal method that displays the current vehicles in ascending order of their id
4. def _checkTruckRec(self, tNode, Uid): This function reads the vehicle id from the
promptsPS2.txt file to be searched for availability in the system. The id is mentioned with the
tag as shown below.
checkTruckRec: 31
checkTruckRec: 542The search function is called for every checkTruckRec tag the program finds in the
promptsPS2.txt file.
If the vehicle id is found with an odd counter, the below string is output to the into the
outputPS2.txt file
Vehicle id xx entered yy times into the system. It is currently fulfilling an open order
If the vehicle id is found with an even counter, the below string is output to the into the
outputPS2.txt file
Vehicle id xx entered yy times into the system. It just completed an order
If the vehicle id is found but counter is 0, the below string is output into the outputPS2.txt file
Vehicle id xx just reached the warehouse
If the vehicle id is not found it outputs the below string into the outputPS2.txt file
Vehicle id xx did not come to the warehouse today
Use a trigger function to call this recursive function from the root node.
5. def _printOrderStatus(self, targetorders): This function is triggered when the following tag
is encountered in the promptsPS2.txt file
printOrderStatus: 11
This function prints the number of open, closed and yet to be fulfilled orders out of the total
target orders into the outputPS2.txt file.
The following status of xx orders:
Open Orders: 2
Closed Orders: 2
Yet to be fulfilled: 7
6. def _highFreqTrucks(self, tNode, frequency): This function generates the list of vehicles
that have moved in/out of the warehouse more than ‘z’ number of times. This does not
consider the scenario with counter ‘0’ i.e., entering warehouse for the first time. The function
reads the x number from the file promptsPS2.txt with the tag as shown below.
highFreqTrucks: 2
The function outputs the vehicle ids and their entries into the outputPS2.txt file as:
Vehicles that moved in/out more than xx times are:
Vehicle id, counter
If no qualifying vehicle print: ‘No such vehicle present in the system’
Use a trigger function to call this recursive function from the root node.7. def _maxDeliveries(self, tNode): This function prints the count and list of vehicle ids that
have completed their maximum deliveries for the day. Allowed maximum deliveries per truck
is determined by the first line of the inputPS2.txt and is triggered with the following tag in the
promptsPS2.txt as shown below.
maxDeliveries
This function prints the list of qualifying vehicle ids into the file outputPS2.txt.
If the maximum allowed orders to be fulfilled by each vehicle is 2, the output file should show:
maxDeliveries: 2
xx Vehicle Ids did their maximum deliveries:
34
Ensure that you use a traversal method that displays the sequence of vehicles in ascending
order of vehicle id.
8. def _availTrucks(self, tNode): This function prints the count and list of vehicle ids that are
currently in the warehouse and available to deliver supplies. If a vehicle is in the warehouse
but already completed its maximum deliveries for the day, then that vehicle is no longer
available for service. It is triggered with the tag in promptsPS2.txt as shown below.
availTrucks
This function prints the qualifying ids into the file outputPS2.txt.
If the maximum allowed orders to be fulfilled by each vehicle is 2, the output file should show:
xx Vehicle Ids that are currently available to deliver supplies:
56
231
643
Ensure that you use a traversal method that displays the sequence of vehicles in ascending
order of vehicle id.
Note that the input/output data shown here is only for understanding and testing, the actual
file used for evaluation will be different.Sample file formats
Sample Input file
First input row indicates the maximum allowed deliveries. Each subsequent row will have one
vehicle id. The input file name must be called inputPS2.txt.
Sample inputPS2.txt
2
34
453
56
34
643
231
31
31
453
34
34
34
Sample promptsPS2.txt
printTruckRec
checkTruckRec: 31
checkTruckRec: 542
printOrderStatus: 11
highFreqTrucks: 2
maxDeliveries
availTrucks
updateTruckRec: 112
updateTruckRec: 453
printTruckRecSample outputPS2.txt
------------- printTruckRec ---------------
Total number of vehicles entered in the warehouse: 6
31, 1
34, 4
56, 0
231, 0
453, 1
643, 0
-----------------------------------------------
------------- checkTruckRec: 31 ---------------
Vehicle id 31 entered 1 time into the system. It is currently fulfilling an open order
-----------------------------------------------
------------- checkTruckRec: 542 ---------------
Vehicle id 542 did not come to the warehouse today
-----------------------------------------------
------------- printOrderStatus: 11 ---------------
The following status of 11 orders:
Open Orders: 2
Closed Orders: 2
Yet to be fulfilled: 7
-----------------------------------------------
------------- highFreqTrucks: 2 ---------------
Vehicles that moved in/out more than 2 times are:
34, 4
-----------------------------------------------
------------- maxDeliveries ---------------
maxDeliveries: 2
1 Vehicle Ids did their maximum deliveries:
34
-----------------------------------------------
------------- availTrucks ---------------
3 Vehicle Ids that are currently available to deliver supplies:
56
231643
-----------------------------------------------
------------- updateTruckRec: 112 ---------------
Vehicle Id 112 record updated
-----------------------------------------------
------------- updateTruckRec: 453---------------
Vehicle Id 453 record updated
-----------------------------------------------
------------- printTruckRec ---------------
Total number of vehicles entered in the warehouse: 7
31, 1
34, 4
56, 0
112, 0
231, 0
453, 2
643, 0
-----------------------------------------------
Note that the input/output data shown here is only for understanding and testing, the actual
file used for evaluation will be different.
2. Deliverables
1. Word document designPS2_<group id>.docx detailing your design and time complexity of
the algorithm.
2. [Group id]_Contribution.xlsx mentioning the contribution of each student in terms of
percentage of work done. Download the Contribution.xlsx template from the link shared in the
Assignment Announcement.
3. inputPS2.txt file used for testing
4. promptsPS2.txt file used for testing
5. outputPS2.txt file generated while testing
6. .py file containing the python code. Create a single *.py file for code. Do not fragment your
code into multiple files
Zip all of the above files including the design document and contribution file in a folder with
the name:
[Group id]_A1_PS2_VehicleRecords.zip and submit the zipped file.Group Id should be given as Gxxx where xxx is your group number. For example, if your group
is 26, then you will enter G026 as your group id.
3. Instructions
1. It is compulsory to make use of the data structure(s) / algorithms mentioned in the problem
statement.
2. Ensure that all data structure insert and delete operations throw appropriate messages when
their capacity is empty or full. Also ensure basic error handling is implemented.
3. For the purposes of testing, you may implement some functions to print the data structures or
other test data. But all such functions must be commented before submission.
4. Make sure that your read, understand, and follow all the instructions
5. Ensure that the input, prompt and output file guidelines are adhered to. Deviations from the
mentioned formats will not be entertained.
6. The input, prompt and output samples shown here are only a representation of the syntax to
be used. Actual files used to evaluate the submissions will be different. Hence, do not hard
code any values into the code.
7. Run time analysis is to be provided in asymptotic notations and not timestamp based runtimes
in sec or milliseconds.
8. Please note that the design document must include
a. The data structure model you chose with justifications
b. Details of each operations with the time complexity and reasons why the chosen
operations are efficient for the given representation
c. One alternate way of modelling the problem with the cost implications.
9. Writing good technical report and well document code is an art. Your report cannot exceed 4
pages. Your code must be modular and quite well documented.
Instructions for use of Python:
1. Implement the above problem statement using Python 3.7.
2. Use only native data types like lists and tuples in Python, do not use dictionaries provided in
Python. Use of external libraries like graph, numpy, pandas library etc. is not allowed. The
purpose of the assignment is for you to learn how these data structures are constructed and
how they work internally.
3. Create a single *.py file for code. Do not fragment your code into multiple files.
4. Do not submit a Jupyter Notebook (no *.ipynb). These submissions will not be evaluated.
5. Read the input file and create the output file in the root folder itself along with your .py file. Do
not create separate folders for input and output files.4. Deadline
1. The strict deadline for submission of the assignment is Monday, 21th Jun, 2021.
2. The deadline has been set considering extra days from the regular duration in order to
accommodate any challenges you might face. No further extensions will be entertained.
3. Late submissions will not be evaluated.
5. How to submit
1. This is a group assignment.
2. Each group has to make one submission (only one, no resubmission) of solutions.
3. Each group should zip all the deliverables in one zip file and name the zipped file as mentioned
above.
4. Assignments should be submitted via Canvas > Assignment section. Assignment submitted
via other means like email etc. will not be graded.
6. Evaluation
1. The assignment carries 12 Marks.
2. Grading will depend on
a. Fully executable code with all functionality working as expected
b. Well-structured and commented code
c. Accuracy of the run time analysis and design document.
3. Every bug in the functionality will have negative marking.
4. Marks will be deducted if your program fails to read the input file used for evaluation due to
change / deviation from the required syntax.
5. Use of only native data types and avoiding libraries like numpy, graph and pandas will get
additional marks.
6. Plagiarism will not be tolerated. Copy / Paste’s from web resources / or your friends’
submission will attract severe penalty to the extent of awarding negative 10 percent. We
will not measure the extent of such blatant copy pastes and details of who copied from
whom and such details while awarding the penalties. It’s the responsibility of the team
to solve and protect your original work.
7. Source code files which contain compilation errors will get at most 25% of the value of that
question
