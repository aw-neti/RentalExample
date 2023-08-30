# RentalExample
RentalExample is a scooter rental example application built in Daml.

### I. Overview 
Project was created by using the "empty-skeleton" template.

Renter can create a RentRequest contract. Owner provided with some RentRequest contracts can exercise Accept or Reject on them to make a RentalDeal contract when accepted or provide some response text when rejecting the request. Additionally Owner can exercise PreviousDeals on RentRequest to see Renter's previous deals recipes and have a possibility to create Scooter contracts for himself to keep important data and condition notes for each scooter to judge if scooter can be rented or not.
Renter after his request is accepted can exercise CanFinishDeal to check if the deal can be finished and FinishDeal to finish and archive the deal after the end of the rental, RentalRecipe will be created then. Renter can also archive the rejected contracts when exercising RemoveRequest.
RentalRecipe is created on FinishDeal to provide history of previous rental deals for specific party.


### II. Workflow
   
      1. Renter creates two RentRequest contracts for renting two different scooters on different dates:
      2a. Owner exercises PreviousDeals to check renter history to see if he already made some deals
      2b. Owner queries his Scooter contracts to see if they have some condition notes so he can know if he can rent them or not
      2c. Owner exercises Accept to one of the requests, RentalDeal is created
      2d. Owner exercises Reject to the second request with the response comment "Scooter is unavailable between 14 and 16 Aug"
      3a. Renter exercises CanFinishDeal to check if he can finish the rental deal
      3b. Renter exercises FinishDeal to finish accepted deal after the end time, RentalRecipe is created
      3c. Renter exercises RemoveRequest to remove/cancel rejected request

### III. Challenge(s)
* The project was created by using `empty-skeleton` and the following was removed from `daml.yaml`:
```
sandbox-options:
   - --wall-clock-time
```

### IV. Compiling & Testing
To compile and test, run the test scripts in the `TestScripts.daml` under /daml or run:
```
$ daml start
```