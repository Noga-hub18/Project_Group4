=======================================================================================================================================
Group Number: 4
=======================================================================================================================================
Group Members:
    1. Full Name: Noga Feldman     , Id Number: 212146740 , Braude's Email: Noga.feldman@e.braude.ac.il
    2. Full Name: Saed Khatib      , Id Number: 324919166 , Braude's Email: Saed.Khatib@e.braude.ac.il
    3. Full Name: Oriyan Eliguev   , Id Number: 325424166 , Braude's Email: Oriyan.Eliguev@e.braude.ac.il
    4. Full Name: Mohammad Nawatha , Id Number: 325218477 , Braude's Email: Mohammad.Nawatha@e.braude.ac.il
    5. Full Name: Ilya Kaganovski  , Id Number: 320533490 , Braude's Email: Ilya.Kaganvski@e.braude.ac.il

---------------------------------------------------------------------------------------------------------------------------------------
# CrisisSync – Scenario Requirements

## Scenario 1: Reserving a resource package for a task, including reporting task completion

| Req ID | Requirement Description (Clean English with "shall") | Type (FR/NFR) | Mapped Use Case | Test ID |
| :--- | :--- | :---: | :--- | :---: |
| **REQ-01** | The resource package always includes exactly one Field Commander, who is responsible for the task. | NFR | Build Task Tree | TEST-01 |
| **REQ-02** | A task cannot reserve resources until all of its prerequisite tasks are completed. | NFR | Define Task Dependencies | TEST-02 |
| **REQ-03** | Resources can be reserved for a task only when the task is in Ready state. | NFR | Manage Task Lifecycle | TEST-03 |
| **REQ-04** | The system shall allow reserving resources. | FR | Reserve Resources | TEST-04 |
| **REQ-05** | Resources can be reserved manually or automatically. | NFR | Reserve Resources | TEST-05 |
| **REQ-06** | Only a Dispatcher can reserve resources. | NFR | Reserve Resources | TEST-06 |
| **REQ-07** | The Dispatcher performs reservation, task cancellation, and event closing and cancellation from the status screens. | NFR | Track Live Event Status | TEST-07 |
| **REQ-08** | Package reservation is all-or-nothing: if any resource is unavailable, the transaction is fully rolled back and no resource is reserved. | NFR | Rollback Reservation Resources | TEST-08 |
| **REQ-09** | A task moves to Active when the Dispatcher reserves its entire resource package in a single transaction. | NFR | Manage Task Lifecycle | TEST-09 |
| **REQ-10** | If any resource in the package is unavailable, the entire reservation fails and the task remains in Ready state. | NFR | Manage Task Lifecycle | TEST-10 |
| **REQ-11** | The possible statuses of a crew member are Available, Reserved for Task or Unavailable only. | NFR | Manage Personnel Pool | TEST-11 |
| **REQ-12** | The possible statuses of an equipment item are Available, Reserved for Task or Faulty/Under Repair only. | NFR | Manage Equipment Pool | TEST-12 |
| **REQ-13** | A resource is either a crew member or an equipment item. | NFR | Manage Equipment Pool | TEST-13 |
| **REQ-14** | Each resource is reserved for at most one task at any moment. | NFR | Reserve Resources | TEST-14 |
| **REQ-15** | A reserved Field Commander cannot be reserved for another task at the same time. | NFR | Reserve Resources | TEST-15 |
| **REQ-16** | An equipment item in Faulty/Under Repair status cannot be reserved. | NFR | Reserve Resources | TEST-16 |
| **REQ-17** | A crew member with exceptional availability cannot be reserved. | NFR | Reserve Resources | TEST-17 |
| **REQ-18** | When two stations attempt to reserve the same resource simultaneously, only one reservation succeeds. | NFR | Reserve Resources | TEST-18 |
| **REQ-19** | A Dispatcher whose reservation failed receives a clear message, and their screen is refreshed to the current state. | NFR | Reserve Resources | TEST-19 |
| **REQ-20** | The system shall allow automatic allocation of resources. | FR | Auto-Allocate Resources | TEST-20 |
| **REQ-21** | Automatic allocation is performed according to a criterion selected by the Dispatcher. | NFR | Auto-Allocate Resources | TEST-21 |
| **REQ-22** | When two allocations for different events select the same resource concurrently, only one receives it. | NFR | Auto-Allocate Resources | TEST-22 |
| **REQ-23** | The allocation that did not receive the resource automatically continues to the next best available alternative, without the Dispatcher resubmitting the request. | NFR | Auto-Allocate Resources | TEST-23 |
| **REQ-24** | The number of alternative allocation attempts is at most 2. | NFR | Auto-Allocate Resources | TEST-24 |
| **REQ-25** | Automatic allocation fails only if no alternative is available in the pool. | NFR | Auto-Allocate Resources | TEST-25 |
| **REQ-26** | The system shall allow tracking events. | FR | Track Live Event Status | TEST-26 |
| **REQ-27** | Event tracking is performed in real time. | NFR | Track Live Event Status | TEST-27 |
| **REQ-28** | The system shall allow opening a live status screen. | FR | Track Live Event Status | TEST-28 |
| **REQ-29** | For each task, the status screen displays its state, Field Commander, reserved resources, and elapsed execution time versus estimated duration. | NFR | Track Live Event Status | TEST-29 |
| **REQ-30** | The system shall allow viewing tasks. | FR | View Commander Tasks | TEST-30 |
| **REQ-31** | Only a Field Commander can view the tasks for which they are appointed commander. | NFR | View Commander Tasks | TEST-31 |
| **REQ-32** | A Field Commander is both an active system user and a personnel resource. | NFR | Manage Personnel Pool | TEST-32 |
| **REQ-33** | A Field Commander who is reserved for a task continues to work in the system as usual. | NFR | View Commander Tasks | TEST-33 |
| **REQ-34** | A Field Commander sees only the status screens of events in which they are responsible for a task, and closes their tasks from them. | NFR | Track Live Event Status | TEST-34 |
| **REQ-35** | The system shall allow reporting task completion. | FR | Complete Task | TEST-35 |
| **REQ-36** | Only the Field Commander appointed to a task can report its completion. | NFR | Complete Task | TEST-36 |
| **REQ-37** | Upon a completion report, the task moves to Completed state. | NFR | Complete Task | TEST-37 |
| **REQ-38** | Upon task completion, the server immediately releases its resources back to Available. | NFR | Complete Task | TEST-38 |
| **REQ-39** | Upon task completion, the server moves to Ready every dependent task whose prerequisite tasks are all completed. | NFR | Complete Task | TEST-39 |
| **REQ-40** | Completed and Cancelled are final states. | NFR | Manage Task Lifecycle | TEST-40 |

## Scenario 2: Generating the on-time performance and service level (SLA) report

| Req ID | Requirement Description (Clean English with "shall") | Type (FR/NFR) | Mapped Use Case | Test ID |
| :--- | :--- | :---: | :--- | :---: |
| **REQ-41** | The system shall allow generating reports. | FR | Generate Reports | TEST-41 |
| **REQ-42** | The report types are a Resource Utilization report and an SLA (on-time performance) report. | NFR | Generate Reports | TEST-42 |
| **REQ-43** | Reports are generated automatically at the end of every month. | NFR | Generate Reports | TEST-43 |
| **REQ-44** | The SLA report displays the average time from event opening until its last task is closed, broken down by event type. | NFR | Generate Reports | TEST-44 |
| **REQ-45** | The system shall allow viewing reports. | FR | View Reports | TEST-45 |
| **REQ-46** | Only a System Administrator can view reports. | NFR | View Reports | TEST-46 |
| **REQ-47** | The system shall allow generating a report on demand. | FR | Generate Reports | TEST-47 |
| **REQ-48** | An on-demand report can be generated for a selected past month. | NFR | Generate Reports | TEST-48 |
| **REQ-49** | Only a System Administrator can generate an on-demand report. | NFR | Generate Reports | TEST-49 |
| **REQ-50** | The event type is selected from a closed list: Building Collapse, Fire, Road Accident, HazMat Leak, Natural Disaster. | NFR | Open New Event | TEST-50 |
| **REQ-51** | The event opening time is recorded automatically. | NFR | Open New Event | TEST-51 |
| **REQ-52** | Each history record includes the exact timestamp and the user who performed the action. | NFR | View Event History and Timeline | TEST-52 |


# CrisisSync – Acceptance Tests (BDD)

Each test ID matches its requirement ID in the traceability matrix (TEST-XX ↔ REQ-XX).

## Scenario 1: Reserving a resource package for a task, including reporting task completion

**Acceptance Test [TEST-01]: Resource Package Without Exactly One Field Commander (Exception / Validation)**
- **Given:** A Dispatcher is defining the resource package of a new task.
- **When:** The Dispatcher saves a package that includes two Field Commanders.
- **Then:** The system must reject the package.
- **And:** The system must display a message stating that a package must include exactly one Field Commander.

**Acceptance Test [TEST-02]: Reservation Blocked by Incomplete Prerequisites (Exception)**
- **Given:** Task B depends on Task A, and Task A is still Active.
- **When:** The Dispatcher tries to reserve the resource package of Task B.
- **Then:** The system must reject the reservation.
- **And:** Task B must remain in Blocked state with no resources reserved.

**Acceptance Test [TEST-03]: Reservation Attempt Outside Ready State (Exception)**
- **Given:** A task is already in Completed state.
- **When:** The Dispatcher tries to reserve resources for that task.
- **Then:** The system must reject the reservation.
- **And:** The task state and the status of all resources must remain unchanged.

**Acceptance Test [TEST-04]: Manual Reservation of a Resource Package (Happy Path)**
- **Given:** A Dispatcher is logged in, a task is in Ready state, and every resource in its package is Available.
- **When:** The Dispatcher selects a specific resource for each item in the package and confirms the reservation.
- **Then:** The system must change the status of every selected resource to Reserved for Task.
- **And:** The system must link all reserved resources to the task.

**Acceptance Test [TEST-05]: Choice Between Manual and Automatic Reservation (Happy Path)**
- **Given:** A task is in Ready state.
- **When:** The Dispatcher starts a reservation for the task.
- **Then:** The system must offer both a manual reservation option and an automatic allocation option.
- **And:** Either option must complete the reservation of the full package.

**Acceptance Test [TEST-06]: Reservation by an Unauthorized User (Exception / Permission)**
- **Given:** A Logistics & Resources Officer is logged in.
- **When:** The officer tries to send a reservation request for a task.
- **Then:** The system must reject the request with a permission error.
- **And:** No resource status may change.

**Acceptance Test [TEST-07]: Reservation From the Status Screen (Happy Path)**
- **Given:** A Dispatcher is viewing the status screen of an open event that has a task in Ready state.
- **When:** The Dispatcher selects the task and chooses Reserve.
- **Then:** The system must start the reservation process from the status screen.
- **And:** After a successful reservation, the status screen must show the reserved resources for that task.

**Acceptance Test [TEST-08]: All-or-Nothing Rollback (Exception / Recovery)**
- **Given:** A task's package includes three resources, and one of them was marked Faulty/Under Repair a moment before.
- **When:** The Dispatcher confirms the reservation of the package.
- **Then:** The system must roll back the entire transaction.
- **And:** The other two resources must remain Available and not be reserved.

**Acceptance Test [TEST-09]: Task Moves to Active After Successful Reservation (Happy Path)**
- **Given:** A task is in Ready state and all resources in its package are Available.
- **When:** The Dispatcher reserves the entire package in a single transaction.
- **Then:** The system must change the task state to Active.
- **And:** All resources in the package must be in Reserved for Task status.

**Acceptance Test [TEST-10]: Failed Reservation Keeps Task in Ready (Exception)**
- **Given:** A task is in Ready state, and one crew member in its package is Unavailable.
- **When:** The Dispatcher tries to reserve the package.
- **Then:** The system must fail the reservation.
- **And:** The task must remain in Ready state.

**Acceptance Test [TEST-11]: Invalid Crew Member Status (Exception / Validation)**
- **Given:** A crew member exists in the personnel pool.
- **When:** A user tries to set the crew member's status to a value outside Available, Reserved for Task or Unavailable.
- **Then:** The system must reject the value.
- **And:** The crew member's previous status must be kept.

**Acceptance Test [TEST-12]: Invalid Equipment Status (Exception / Validation)**
- **Given:** An equipment item exists in the equipment pool.
- **When:** A user tries to set the item's status to a value outside Available, Reserved for Task or Faulty/Under Repair.
- **Then:** The system must reject the value.
- **And:** The item's previous status must be kept.

**Acceptance Test [TEST-13]: Package Item That Is Not a Resource (Exception / Validation)**
- **Given:** A Dispatcher is defining a resource package.
- **When:** The Dispatcher tries to add an item that is neither a crew role nor an equipment type.
- **Then:** The system must reject the item.
- **And:** The package must contain only crew members and equipment items.

**Acceptance Test [TEST-14]: Resource Already Reserved for Another Task (Exception)**
- **Given:** A bulldozer is reserved for Task A, which is Active.
- **When:** The Dispatcher tries to reserve the same bulldozer for Task B.
- **Then:** The system must reject the reservation for Task B.
- **And:** The bulldozer must remain reserved only for Task A.

**Acceptance Test [TEST-15]: Reserved Field Commander Selected Again (Exception)**
- **Given:** A Field Commander is reserved for an Active task.
- **When:** The Dispatcher tries to include the same Field Commander in another task's package.
- **Then:** The system must reject the reservation.
- **And:** The system must indicate that the Field Commander is not available.

**Acceptance Test [TEST-16]: Faulty Equipment Not Reservable (Exception)**
- **Given:** An ambulance is in Faulty/Under Repair status.
- **When:** The Dispatcher reserves a package that requires an ambulance.
- **Then:** The system must not offer the faulty ambulance as a candidate.
- **And:** A direct attempt to reserve the faulty ambulance must be rejected.

**Acceptance Test [TEST-17]: Crew Member on Sick Leave Not Reservable (Exception)**
- **Given:** A paramedic's exceptional availability is set to Sick Leave.
- **When:** The Dispatcher tries to reserve the paramedic for a task.
- **Then:** The system must reject the reservation.
- **And:** The paramedic's status must remain unchanged.

**Acceptance Test [TEST-18]: Simultaneous Reservation From Two Stations (Exception / Concurrency)**
- **Given:** Two Dispatchers at two stations are reserving packages for different tasks, and both include the same Available bulldozer.
- **When:** Both Dispatchers confirm their reservation at the same moment.
- **Then:** Exactly one reservation must succeed.
- **And:** The bulldozer must be reserved for one task only.

**Acceptance Test [TEST-19]: Recovery After Losing a Reservation Race (Exception / Recovery)**
- **Given:** A Dispatcher's reservation failed because another station reserved the same resource first.
- **When:** The system returns the result to the Dispatcher.
- **Then:** The Dispatcher must receive a clear message naming the resource that was not available.
- **And:** The Dispatcher's screen must refresh to the current state, with the task still in Ready state and available for a new reservation.

**Acceptance Test [TEST-20]: Automatic Allocation of a Full Package (Happy Path)**
- **Given:** A task is in Ready state and the pool has enough Available resources for its package.
- **When:** The Dispatcher requests automatic allocation.
- **Then:** The system must select and reserve a resource for every item in the package.
- **And:** The task must move to Active.

**Acceptance Test [TEST-21]: Allocation by the Selected Criterion (Happy Path)**
- **Given:** Three Available fire trucks are located at different distances from the event location.
- **When:** The Dispatcher selects the "closest to the event" criterion and requests automatic allocation.
- **Then:** The system must reserve the fire truck closest to the event location.
- **And:** The other two fire trucks must remain Available.

**Acceptance Test [TEST-22]: Two Allocations Competing for the Same Resource (Exception / Concurrency)**
- **Given:** Automatic allocations for two different events both select the same generator as their best choice.
- **When:** Both allocations run at the same time.
- **Then:** Only one allocation must receive the generator.
- **And:** The generator must be reserved for one task only.

**Acceptance Test [TEST-23]: Automatic Fallback to the Next Alternative (Exception / Recovery)**
- **Given:** An automatic allocation lost its first-choice generator to another allocation, and another generator is Available.
- **When:** The system detects the conflict.
- **Then:** The system must automatically reserve the next best Available generator.
- **And:** The Dispatcher must not be required to resubmit the request.

**Acceptance Test [TEST-24]: Alternative Attempt Limit (Exception / Retry Limit)**
- **Given:** An automatic allocation lost its first choice, and each alternative it selects is also taken by another allocation.
- **When:** The system has made 2 alternative attempts.
- **Then:** The system must not make a third alternative attempt.
- **And:** The Dispatcher must be informed that the allocation did not complete.

**Acceptance Test [TEST-25]: No Alternative Available in the Pool (Exception)**
- **Given:** A task requires a bulldozer and no bulldozer in the pool is Available.
- **When:** The Dispatcher requests automatic allocation.
- **Then:** The system must fail the allocation.
- **And:** The Dispatcher must be informed of the failure and the task must remain in Ready state.

**Acceptance Test [TEST-26]: Tracking Open Events (Happy Path)**
- **Given:** Two events are open, each with tasks in different states.
- **When:** The Dispatcher opens event tracking.
- **Then:** The system must display both open events.
- **And:** The Dispatcher must be able to select an event to see its status.

**Acceptance Test [TEST-27]: Real-Time Update Between Stations (Happy Path)**
- **Given:** A Dispatcher at station A is viewing the status screen of an open event.
- **When:** A Field Commander at station B reports the completion of a task in that event.
- **Then:** The status screen at station A must show the task as Completed.
- **And:** The update must appear without the Dispatcher refreshing the screen.

**Acceptance Test [TEST-28]: Opening a Live Status Screen (Happy Path)**
- **Given:** A Dispatcher is logged in and an event is open.
- **When:** The Dispatcher selects the event.
- **Then:** The system must open the live status screen of that event.
- **And:** The screen must show the event's current task tree.

**Acceptance Test [TEST-29]: Task Details on the Status Screen (Happy Path)**
- **Given:** A task in an open event is Active, with a Field Commander and reserved resources.
- **When:** The Dispatcher views the event's status screen.
- **Then:** The system must display the task's state, Field Commander and reserved resources.
- **And:** The system must display the elapsed execution time next to the estimated duration.

**Acceptance Test [TEST-30]: Field Commander Views Their Tasks (Happy Path)**
- **Given:** A Field Commander is appointed to two tasks.
- **When:** The Field Commander logs in and opens the task view.
- **Then:** The system must display both tasks.
- **And:** Each task must show its current state.

**Acceptance Test [TEST-31]: Access to Another Commander's Task (Exception / Permission)**
- **Given:** Field Commander X is logged in, and Task C is commanded by Field Commander Y.
- **When:** Field Commander X tries to open Task C.
- **Then:** The system must deny access.
- **And:** Task C must not appear in Field Commander X's task list.

**Acceptance Test [TEST-32]: Field Commander as User and Resource (Happy Path)**
- **Given:** A Field Commander has a user account in the system.
- **When:** The Logistics & Resources Officer views the personnel pool.
- **Then:** The Field Commander must appear as a personnel resource with the role Field Commander.
- **And:** The same Field Commander must be able to log in with their user account.

**Acceptance Test [TEST-33]: Reserved Field Commander Keeps Working (Happy Path)**
- **Given:** A Field Commander is reserved for an Active task.
- **When:** The Field Commander logs in.
- **Then:** The system must grant full access to the Field Commander's screens.
- **And:** The Field Commander's reserved status must remain unchanged.

**Acceptance Test [TEST-34]: Field Commander Sees Only Relevant Events (Exception / Permission)**
- **Given:** Two events are open, and the Field Commander is responsible for a task in only one of them.
- **When:** The Field Commander opens the status screens.
- **Then:** The system must display only the event in which the Field Commander is responsible for a task.
- **And:** A direct attempt to open the other event's status screen must be denied.

**Acceptance Test [TEST-35]: Reporting Task Completion (Happy Path)**
- **Given:** A Field Commander is appointed to an Active task.
- **When:** The Field Commander reports that the task is complete.
- **Then:** The system must accept the report.
- **And:** The system must confirm the completion to the Field Commander.

**Acceptance Test [TEST-36]: Completion Reported by a Non-Appointed User (Exception / Permission)**
- **Given:** A task is Active and is commanded by Field Commander Y.
- **When:** Field Commander X tries to report the task's completion.
- **Then:** The system must reject the report.
- **And:** The task must remain Active.

**Acceptance Test [TEST-37]: Task Moves to Completed (Happy Path)**
- **Given:** A task is Active.
- **When:** The appointed Field Commander reports its completion.
- **Then:** The system must change the task state to "Completed".
- **And:** The status screen must show the task as Completed.

**Acceptance Test [TEST-38]: Resources Released on Completion (Happy Path)**
- **Given:** An Active task has a reserved ambulance and two paramedics.
- **When:** The task is completed.
- **Then:** The system must immediately change the ambulance and the paramedics to Available.
- **And:** These resources must be available for reservation by other tasks.

**Acceptance Test [TEST-39]: Dependent Task Unblocked on Completion (Happy Path)**
- **Given:** Task B depends only on Task A, Task B is Blocked, and Task A is Active.
- **When:** Task A is completed.
- **Then:** The system must automatically change Task B to Ready.
- **And:** Task B must become available for reservation.

**Acceptance Test [TEST-40]: Change Attempt on a Final-State Task (Exception)**
- **Given:** A task is in Completed state.
- **When:** A user tries to change its state or reserve resources for it.
- **Then:** The system must reject the change.
- **And:** The task must remain Completed.

## Scenario 2: Generating the on-time performance and service level (SLA) report

**Acceptance Test [TEST-41]: Generating a Report (Happy Path)**
- **Given:** A System Administrator is logged in and closed events exist for the previous month.
- **When:** A report is generated for that month.
- **Then:** The system must produce the report.
- **And:** The report must be stored and listed among the generated reports.

**Acceptance Test [TEST-42]: Available Report Types (Happy Path)**
- **Given:** A System Administrator opens the reports screen.
- **When:** The administrator views the report type list.
- **Then:** The list must include the Resource Utilization report and the SLA report.
- **And:** No other report type may appear in the current release.

**Acceptance Test [TEST-43]: Automatic Month-End Generation (Happy Path / Timer)**
- **Given:** The system clock reaches the end of the month.
- **When:** The month ends.
- **Then:** The system must automatically generate the Resource Utilization report and the SLA report for that month.
- **And:** Both reports must be available to the System Administrator without manual action.

**Acceptance Test [TEST-44]: SLA Report Calculation (Happy Path)**
- **Given:** During the month, two Fire events took 4 hours and 6 hours from opening until their last task was closed, and one Road Accident event took 2 hours.
- **When:** The SLA report for that month is generated.
- **Then:** The report must show an average of 5 hours for Fire.
- **And:** The report must show an average of 2 hours for Road Accident.

**Acceptance Test [TEST-45]: Viewing a Generated Report (Happy Path)**
- **Given:** An SLA report has been generated for the previous month.
- **When:** The System Administrator opens the report.
- **Then:** The system must display the report.
- **And:** The report must show the month it covers.

**Acceptance Test [TEST-46]: Report Access by an Unauthorized User (Exception / Permission)**
- **Given:** A Dispatcher is logged in.
- **When:** The Dispatcher tries to open a report.
- **Then:** The system must deny access.
- **And:** The report content must not be displayed.

**Acceptance Test [TEST-47]: On-Demand Report Generation (Happy Path)**
- **Given:** A System Administrator is logged in.
- **When:** The administrator requests an SLA report on demand.
- **Then:** The system must generate the report immediately.
- **And:** The report must be displayed to the administrator.

**Acceptance Test [TEST-48]: On-Demand Report for a Selected Past Month (Happy Path)**
- **Given:** Events were closed in September 2026.
- **When:** The System Administrator selects September 2026 and requests an SLA report on demand.
- **Then:** The system must generate the report for September 2026.
- **And:** The report must include only events from that month.

**Acceptance Test [TEST-49]: On-Demand Generation by an Unauthorized User (Exception / Permission)**
- **Given:** A Logistics & Resources Officer is logged in.
- **When:** The officer tries to generate a report on demand.
- **Then:** The system must reject the request.
- **And:** No report may be generated.

**Acceptance Test [TEST-50]: Event Type Outside the Closed List (Exception / Validation)**
- **Given:** A Dispatcher is opening a new event.
- **When:** The Dispatcher tries to enter an event type that is not in the list, such as "Flood".
- **Then:** The system must not accept the value.
- **And:** The Dispatcher must choose from Building Collapse, Fire, Road Accident, HazMat Leak or Natural Disaster.

**Acceptance Test [TEST-51]: Automatic Recording of Event Opening Time (Happy Path)**
- **Given:** A Dispatcher is opening a new event.
- **When:** The Dispatcher saves the event.
- **Then:** The system must record the opening time automatically from the system clock.
- **And:** The Dispatcher must not be able to enter or edit the opening time.

**Acceptance Test [TEST-52]: History Record With Timestamp and User (Happy Path)**
- **Given:** A Field Commander reports the completion of a task.
- **When:** The task state changes to "Completed".
- **Then:** The system must create a history record of the change.
- **And:** The record must include the exact timestamp and the Field Commander who performed the action.
