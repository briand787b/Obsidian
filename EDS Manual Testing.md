# EDS Manual Testing (Week of 5/17/22)
## Introduction
Tests will run on SS90 and/or Euro Lane (thin client)


## Test Cases

Here are sample test cases:

**Shutdown Lane:**
1. System-Status message will be send with status of system and application.

**Start-Up Scenario:**
1.  Power on Lane
2.  UI will come-up, get resource data from resource service (? https://github.com/ncr-swt-retail/scoxresources)
	1. If UI display disconnected, one or more service are not up and may have issue

               **EDS Validation:**

                              1 - System-State message will be sent if core service, tb service and UI service is up and running.

                              2 - System-Status message will be send with status of system and application.

	2. If UI display lane closed screen, critical services are up and running

               **EDS Validation:**

                              1 - System-State message will be sent.

                              2 - System-Status message will be send with status of system and application.

**Lane Open Scenario:**

1.  Login to lane with valid credentials
2.  UI displayed welcome screen

               **EDS Validation:**

                              1 - System-State message will be sent.

                              2 - In case of Start of Day event, Cash-Activity and Cash-Balance message will be send.

**Lane Close Scenario:**

1. Close Lane
2.  Click on assistance at welcome screen, and login to `store mode` with valid credentials
3.  Click on close lane, lane will be closed

               **EDS Validation:**

                              1 - System-Mode message will be sent with store as true (inside store authorization screen)

							  2 - System-State message will be sent with state as out of service.

                              3 - System-Mode message will be sent with store as false (lane close screen).

**Empty Transaction:**

1.  Touch start to start transaction
2.  Touch pay to finish transaction

               **EDS Validation:**

                              1 - System-State message will be send for each state change.

                             2 - System-Transaction message will be sent with transaction result as empty.

**Normal Transaction:**

1.  Touch start to start transaction
2.  Add one or more item
3.  Touch pay to move to payment screen
4.  Select cash and make cash payment
5.  If over amount inserted then change will be dispensed
6.  Thank you screen displayed. Receipt will be printed
7.  Transaction completed and Lane will move to Welcome screen.

               **EDS Validation:**

                              1 - System-State message will be send for each state change.

                              2 - System-Transaction message will be sent with transaction result as completed.

                              3 - Cash-Activity and Cash-Balance message will be send.

**Cancel Transaction:**

1.  Touch start to start transaction
2.  Add one or more item
3.  Login to store mode and cancel transaction.
4.  Transaction canceled, Lane move to Welcome screen.

               **EDS Validation:**

                              1 - System-State message will be send for each state change.

                             2 - System-Mode message will be send when login to store mode and came-out of store mode.

                              3 - System-Transaction message will be sent with transaction result as cancelled.

                             4 - Cash-Activity and Cash-Balance message will be send.

**Suspend Transaction:**

1.  Touch start to start transaction
2.  Add one or more item
3.  Login to store mode and suspend transaction.
4.  Transaction suspended, Lane move to Welcome screen.

               **EDS Validation:**

                              1 - System-State message will be send for each state change.

                             2 - System-Mode message will be send when login to store mode and came-out of store mode.

                              3 - System-Transaction message will be sent with transaction result as suspended.

                             4 - Cash-Activity and Cash-Balance message will be send.

## Notes
Dag logs print out logs for all jarvis services

## Questions for Ritesh
1.  For this step:  `UI will come-up, get resource data from resource service (? https://github.com/ncr-swt-retail/scoxresources)`,  should I look at the scoxresources logs to see data for varioues jarvis resources?
2. How do we synthesize a `Start of Day event`
3.  Does this refer to a log message or a message displayed to the UI: 1 - System-Mode message will be sent with store as true (inside store authorization screen)