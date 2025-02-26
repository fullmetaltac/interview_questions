# Table of Contents
- [Table of Contents](#table-of-contents)
  - [Chapter 1 - Fundamentals of testing](#chapter-1---fundamentals-of-testing)
    - [Why is testing necessary?](#why-is-testing-necessary)
    - [What is testing?. Testing principles.](#what-is-testing-testing-principles)
    - [Fundamental test process.](#fundamental-test-process)
    - [The psychology of testing.](#the-psychology-of-testing)
    - [SAMPLE EXAM QUESTIONS](#sample-exam-questions)
  - [Chapter 2 - Testing throughout the software life cycle](#chapter-2---testing-throughout-the-software-life-cycle)
    - [Software development models](#software-development-models)
    - [Test levels](#test-levels)
    - [Test types: the targets of testing](#test-types-the-targets-of-testing)
    - [Maintenance testing](#maintenance-testing)
    - [SAMPLE EXAM QUESTIONS](#sample-exam-questions-1)
  - [Chapter 3 - Static techniques](#chapter-3---static-techniques)
    - [Reviews and the test process](#reviews-and-the-test-process)
    - [Review process](#review-process)
    - [Static analysis by tools](#static-analysis-by-tools)
    - [SAMPLE EXAM QUESTIONS](#sample-exam-questions-2)
  - [Chapter 4](#chapter-4)
  - [Chapter 5](#chapter-5)
  - [Chapter 6](#chapter-6)
  - [References:](#references)

---

## Chapter 1 - Fundamentals of testing 

### Why is testing necessary?  

From Section 1.1, you should now be able to explain why testing is necessary  
and support that explanation with examples and evidence. You should be able  
to give examples of negative consequences of a software defect or bug for  
people, companies, and the environment. You should be able to contrast a  
defect with its symptoms. You should be able to discuss the ways in which  
testing fits into and supports higher quality. You should know the glossary terms  
**bug**, **defect**, **error**, **failure**, **fault**, **mistake**, **quality**, **risk**, **software**,  
**testing** and **exhaustive testing**.  

> **defect** - An imperfection or deficiency in a work product where it does not meet its requirements or  
specifications or impairs its intended use.

> **error** - A human action that results in a defect.

> **failure** - An event in which a component or system does not meet its requirements within specified limits.

> **quality** - The degree to which a work product satisfies stated and implied requirements.

> **risk** - A factor that could result in future negative consequences. 

> **testing** - The process within the software development lifecycle that evaluates the quality of a component  
or system and related work products.

> **exhaustive testing** - A test approach in which the test suite comprises all combinations of input values and  
preconditions.

### What is testing?. Testing principles.

From Section 1.2, you should now know what testing is. You should be able  
to remember the common objectives of testing. You should be able to describe  
how testing can find defects, provide confidence and information and prevent  
defects. You should be able to explain the fundamental principles of testing,  
summarized in Section 1.3. You should know the glossary terms **code**, **debugging**,  
**development of software**, **requirement**, **review**, **test basis**,  
**test case**, **testing** and **test objective**.  

> **debugging** - The process of finding, analyzing and removing the causes of failures in a component or system.

> **requirement** - A provision that contains criteria to be fulfilled.

> **review** - A type of static testing in which the quality of a work product or process is evaluated by individuals.

> **test basis** - The body of knowledge used as the basis for test analysis and test design.

> **test case** - A set of preconditions, inputs, actions (where applicable), expected results and postconditions,  
developed based on test conditions.

> **testing** - The process within the software development lifecycle that evaluates the quality of a component or system and related work products.

> **test objective** - The purpose for testing.

### Fundamental test process.

From Section 1.4, you should now recognize the fundamental test process, as  
well as being aware of some other related ways to model the test process. You  
should be able to recall the main testing activities related to test planning and  
control, analysis and design, implementation and execution, evaluating exit criteria and reporting, and test closure.   
You should know the glossary terms **confirmation testing**, **exit criteria**, **incident**, **regression testing**,   
**test basis**, **test condition**, **test coverage**, **test data**, **test execution**, **test log**, **test plan**,  
**test strategy**, **test summary report** and **testware**.

> **confirmation testing** - A type of change-related testing performed after fixing a defect to confirm that a  
failure caused by that defect does not reoccur.

> **exit criteria** - The set of conditions for officially completing a defined task.

> **regression testing** - A type of change-related testing to detect whether defects have been introduced  
or uncovered in unchanged areas of the software.

> **test basis** - The body of knowledge used as the basis for test analysis and test design.

> **test condition** - A testable aspect of a component or system identified as a basis for testing.

> **coverage** - The degree to which specified coverage items are exercised by a test suite, expressed  
as a percentage.

> **test data** - Data needed for test execution.

> **test execution** - The activity that runs a test on a component or system producing actual results.

> **test log** - A chronological record of relevant details about the execution of tests.

> **test plan** - Documentation describing the test objectives to be achieved and the means and the schedule  
for achieving them, organized to coordinate testing activities.

> **test strategy** - A description of how to perform testing to reach test objectives under given circumstances.

> **test completion report** -A type of test report produced at completion milestones that provides an evaluation of  
the corresponding test items against exit criteria.

> **testware** - Work products produced during the test process for use in planning, designing, executing, evaluating  
and reporting on testing.

### The psychology of testing.

Finally, from Section 1.5, you now should be able to explain the psychology  
of testing and how people influence testing success. You should recall the  
importance of clear objectives, the right mix of self-testing and independent  
testing and courteous, respectful communication between testers and others on  
the project team, especially about defects. You should be able to explain and  
contrast the mindsets of testers and programmers and why these differences can  
lead to conflicts. You should know the glossary term **independence**  

> **independence of testing** - Separation of responsibilities, which encourages the accomplishment of  
objective testing.

### SAMPLE EXAM QUESTIONS

1) A company recently purchased a commercial off-the-shelf application to automate  
their bill-paying process. They now plan to run an acceptance test against the package prior to  
putting it into production. Which of the following is their most likely reason for testing?  

1. To build confidence in the application.
1. To detect bugs in the application.
1. To gather evidence for a lawsuit.
1. To train the users
    <details><summary>Answer:</summary>1</details></br>

2) According to the ISTQB Glossary, the word **bug** is synonymous with which of the following words?

1. Incident
1. Defect
1. Mistake
1. Error
    <details><summary>Answer:</summary>2</details></br>

3) According to the ISTQB Glossary, a **risk** relates to which of the following?

1. Negative feedback to the tester.
1. Negative consequences that will occur.
1. Negative consequences that could occur.
1. Negative consequences for the test object.
    <details><summary>Answer:</summary>3</details></br>

4) Ensuring that test design starts during the requirements definition phase is important to enable which  
of the following test objectives?

1. Preventing defects in the system.
1. Finding defects through dynamic testing.
1. Gaining confidence in the system.
1. Finishing the project on time.
    <details><summary>Answer:</summary>1</details></br>

5) A test team consistently finds between 90% and 95% of the defects present in  
the system under test. While the test manager understands that this is a good defect-detection  
percentage for her test team and industry, senior management and executives remain disappointed  
in the test group, saying that the test team misses too many bugs. Given that the users are generally  
happy with the system and that the failures which have occurred have generally been low impact,  
which of the following testing principles is most likely to help the test manager explain to these  
managers and executives why some defects are likely to be missed?  

1. Exhaustive testing is impossible
1. Defect clustering
1. Pesticide paradox
1. Absence-of-errors fallacy
    <details><summary>Answer:</summary>1</details></br>

6) According to the ISTQB Glossary, regression testing is required for what purpose?

1. To verify the success of corrective actions.
1. To prevent a task from being incorrectly considered completed.
1. To ensure that defects have not been introducedby a modification.
1. To motivate better unit testing by the programmers.
    <details><summary>Answer:</summary>3</details></br>

7) Which of the following is most important to promote and maintain good relationships between   
testers and developers?

1. Understanding what managers value about testing.
1. Explaining test results in a neutral fashion.
1. Identifying potential customer work-arounds for bugs.
1. Promoting better quality software whenever possible.
    <details><summary>Answer:</summary>2</details></br>

8) Which of the statements below is the best assessment of how the test principles apply   
across the test life cycle?

1. Test principles only affect the preparation for testing.
1. Test principles only affect test execution activities.
1. Test principles affect the early test activities such as review.
1. Test principles affect activities throughout the test life cycle.
    <details><summary>Answer:</summary>4</details></br>

## Chapter 2 - Testing throughout the software life cycle

### Software development models

From Section 2.1, you should now understand the relationship
between development and testing within a development life cycle,
including the test activities and test (work) products. You should
know that the development model to use should fit, or must be
adapted to fit, the project and product characteristics. You should
be able to recall the reasons for different levels of testing and
characteristics of good testing in any life cycle model. You should
know the glossary terms (**commercial**) **off-the-shelf software**
(**COTS**), **incremental development model**, **test level**, **validation**,
**verification** and **V-model**.

> **commercial off-the-shelf** - A type of product developed in an identical format for a large number  
of customers in the general market. 

> **incremental development model** - A type of software development lifecycle model in which the component  
or system is developed through a series of increments.

> **test level** - A specific instantiation of a test process.

> **validation** - Confirmation by examination that a work product matches a stakeholder's needs.

> **verification** - The process of confirming that a work product fulfills its specification.

> **V-model** - A sequential software development lifecycle model describing a one-for-one relationship between major  
phases of software development from business requirements specification to delivery, and corresponding test levels  
from acceptance testing to component testing.

### Test levels

From Section 2.2, you should know the typical levels of testing. You should be able to compare the different levels   
of testing with respect to their major objectives, typical objects of testing, typical targets of testing (e.g.   
functional or structural) and related work products. You should also know which persons perform the testing   
activities at the various test levels, the types of defects found and failures to be identified. You should know the  
glossary terms **alpha testing**, **beta testing**, **component testing**, **driver**, **functional requirements**,   
**integration**, **integration testing**, **non-functional testing**, **operational testing**, **regulation acceptance  testing** (**compliance testing**),  
**robustness testing**, **stub**, **system testing**, **test-driven development**, **test environment** and **user acceptance testing**.

> **alpha testing** - A type of acceptance testing performed in the developer's test environment by roles outside the  
 development organization.

> **beta testing** - A type of acceptance testing performed at an external site to the developer's test environment by  
roles outside the development organization.

> **component testing** - A test level that focuses on individual hardware or software components.

> **driver** - A component or tool that temporarily replaces another component and controls or calls a test item in   
isolation.

> **integration testing** - A test level that focuses on interactions between components or systems.

> **non-functional testing** - Testing performed to evaluate that a component or system complies with non-functional requirements.

> **compliance testing** - Testing to determine the compliance of the component or system.

> **stub** - A type of test double providing predefined responses.

> **system testing** - A test level that focuses on verifying that a system as a whole meets specified requirements.

> **test-driven development** - A software development technique in which the test cases are developed, automated  
and then the software is developed incrementally to pass those test cases.

> **test environment** - An environment containing hardware, instrumentation, simulators, software tools, and other  
support elements needed to perform a test.

> **user acceptance testing** - A type of acceptance testing performed to determine if intended users accept the system.

### Test types: the targets of testing

From Section 2.3, you should know the four major types of test (functional, non-functional, structural and change-related) and should be able to provide some concrete examples for each of these. You should understand that functional and structural tests occur at any test level and be able to explain how they are applied
in the various test levels. You should be able to identify and describe non-functional test types based on non-functional requirements and product quality characteristics. Finally you should be able to explain the purpose of confirmation testing (retesting) and regression testing in the context of change-related testing. You should know the glossary terms **black-box testing**, **code coverage**, **confirmation testing** (**re-testing**), **functional testing**, **interoperability testing**, **load testing**, **maintainability testing**, **performance testing**, **portability testing**, **regression testing**, **reliability testing**, **security testing**, **specification-based testing**, **stress testing**, **structural testing**, **test suite**, **usability testing** and **white-box testing**.

> **black-box testing** - Testing based on an analysis of the specification of the component or system.

> **coverage** - The degree to which specified coverage items are exercised by a test suite, expressed as a percentage.

> **confirmation testing** - A type of change-related testing performed after fixing a defect to confirm that a failure caused by that defect does not reoccur.

> **functional testing** - Testing performed to evaluate if a component or system satisfies functional requirements.

> **interoperability** - The degree to which two or more components or systems can exchange information and use the information that has been exchanged.

> **load testing** - A type of performance testing conducted to evaluate the behavior of a component or system under  
varying loads, usually between anticipated conditions of low, typical, and peak usage.

> **maintainability** - The degree to which a component or system can be modified by the intended maintainers.

> **performance testing** - A test type to determine the performance efficiency of a component or system 

> **portability** - The degree to which a component or system can be transferred from one hardware, software or other operational or usage environment to another.

> **regression testing** -  A type of change-related testing to detect whether defects have been introduced or  
uncovered in unchanged areas of the software.

> **reliability** - The degree to which a component or system performs specified functions under specified   
conditions for a specified period of time.

> **security testing** - A test type to determine the security of a component or system.

> **stress testing** - A type of performance testing conducted to evaluate a system or component at or beyond the limits of its anticipated or specified workloads, or with reduced availability of resources such as access to memory or servers.

> **test suite** - A set of test scripts or test procedures to be executed in a specific test run.

> **usability testing** - Testing to evaluate the degree to which the system can be used by specified users with  
effectiveness, efficiency and satisfaction in a specified context of use.

> **white-box testing** - Testing based on an analysis of the internal structure of the component or system.

### Maintenance testing

From Section 2.4, you should be able to compare maintenancetesting to testing of new applications.   
You should be able to identify triggers and reasons for maintenance testing, such as modifications, migration  
and retirement. Finally you should be able to describe the role of regression testing and impact analysis within  
maintenance testing. You should know the glossary terms **impact analysis** and **maintenance testing**.

> **impact analysis** - The identification of all work products affected by a change, including an estimate of  
the resources needed to accomplish the change

> **maintenance testing** - Testing the changes to an operational system or the impact of a changed environment  
to an operational system.

### SAMPLE EXAM QUESTIONS

1) What are good practices for testing within the development life cycle?
    
1. Early test analysis and design.
1. Different test levels are defined with specific objectives.
1. Testers will start to get involved as soon as coding is done.
1. A and B above.
    <details><summary>Answer:</summary>4</details></br>

2) Which option best describes objectives for test levels with a life cycle model?

1. Objectives should be generic for any test level.
1. Objectives are the same for each test level.
1. The objectives of a test level don't need to be defined in advance.
1. Each level has objectives specific to that level.
    <details><summary>Answer:</summary>4</details></br>

3) Which of the following is a test type?

1. Component testing
1. Functional testing
1. System testing
1. Acceptance testing
    <details><summary>Answer:</summary>2</details></br>

4) Which of the following is a non-functional quality characteristic?

1. Feasibility
1. Usability
1. Maintenance
1. Regression
    <details><summary>Answer:</summary>2</details></br>

5) Which of these is a functional test?

1. Measuring response time on an on-line booking system.
1. Checking the effect of high volumes of traffic in a call-center system.
1. Checking the on-line bookings screen information and the database contents against the   
information on the letter to the customers.
1. Checking how easy the system is to use.
    <details><summary>Answer:</summary>3</details></br>

6) Which of the following is a true statement regarding the process of fixing emergency changes?

1. There is no time to test the change before it goes live, so only the best developers should  
do this work and should not involve testers as they slow down the process.
1. Just run the retest of the defect actually fixed.
1. Always run a full regression test of the whole system in case other parts of the system have  
been adversely affected.
1. Retest the changed area and then use risk assessment to decide on a reasonable subset of the  
whole regression test to run in case other parts of the system have been adversely affected.
    <details><summary>Answer:</summary>4</details></br>

7) A regression test:

1. Is only run once.
1. Will always be automated.
1. Will check unchanged areas of the software to see if they have been affected.
1. Will check changed areas of the software to see if they have been affected.
    <details><summary>Answer:</summary>3</details></br>

8) Non-functional testing includes:

1. Testing to see where the system does not function correctly.
1. Testing the quality attributes of the system including reliability and usability.
1. Gaining user approval for the system.
1. Testing a system feature using only the software required for that function.
    <details><summary>Answer:</summary>2</details></br>

9) Beta testing is:

1. Performed by customers at their own site.
1. Performed by customers at the software developer's site.
1. Performed by an independent test team.
1. Useful to test software developed for a specific customer or user.
    <details><summary>Answer:</summary>1</details></br>

## Chapter 3 - Static techniques

### Reviews and the test process

From Section 3.1, you should be able to explain the importance and advantages of static testing. You should know  
the difference between static testing and dynamic testing, and also understand the concept of reviews. You should  
be able to recognize the software work products that can be examined by static testing. You should know the glossary  
terms **static testing**, **dynamic testing** and **reviews**.

> **static testing** - Testing that does not involve the execution of a test item.

> **dynamic testing** - Testing that involves the execution of the test item.


### Review process

From Section 3.2, you should understand the difference between formal and informal reviews. You should be able to  
recall the main phases of a typical formal review. The main roles within reviews and their responsibilities should  
be clear to you. You should know the differences between the various types of formal review: technical review,  
walkthrough and inspection. Finally you should be able to explain the factors for successful performance of reviews.  
You should know the glossary terms **entry criteria**, **exit criteria**, **formal review**, **informal review**,  
**inspection**, **moderator**, **reviewer**, **scribe**, **technical review** and **walkthrough**.

> **entry criteria** - The set of conditions for officially starting a defined task.

> **exit criteria** - The set of conditions for officially completing a defined task.

> **formal review** - A review that follows a defined process with a formally documented output.

> **informal review** - A type of review that does not follow a defined process and has no formally documented output.

> **inspection** - A type of formal review that uses defined team roles and measurement to identify defects in a work  
product, and improve the review process and the software development process.

> **moderator** - (1) The person responsible for running review meetings. (2) The person who performs a usability  
test session.

> **reviewer** - A participant in a review who identifies defects in the work product.

> **scribe** - A person who records information at a review meeting.

> **technical review** - A formal review by technical experts that examine the quality of a work product and identify  
discrepancies from specifications and standards.

> **walkthrough** - A type of review in which an author leads members of the review through a work product and the  
members ask questions and make comments about possible issues.

### Static analysis by tools 

From Section 3.3, you should understand the objective of static analysis and be able to compare it to static and  
dynamic testing. You should be able to describe the main features of static analysis and recall typical defects that  
can be found using static analysis. Finally, you should be able to recall the benefits of using static analysis. You  
should now the glossary terms **compiler**, **cyclomatic complexity**, **control flow**, **data flow** and  
**static analysis**.

> **cyclomatic complexity** - The maximum number of linear, independent paths through a program.

> **control flow analysis** - A type of static analysis based on a representation of unique paths for executing  
a component or system.

> **data flow analysis** - A type of static analysis based on the lifecycle of variables.

> **static analysis** - The process of evaluating a component or system without executing it, based on its form,  
structure, content, or documentation.

### SAMPLE EXAM QUESTIONS

1) Which of the following artifacts can be examined by using review techniques?

1. Software code
1. Requirements specification
1. Test designs
1. All of the above
    <details><summary>Answer:</summary>4</details></br>

2) Which statement about the function of a static analysis tool is true?

1. Gives quality information about the code without executing it.
1. Checks expected results against actual results.
1. Can detect memory leaks.
1. Gives information about what code has and has not been exercised. 
    <details><summary>Answer:</summary>1</details></br>

3) Which is not a type of review?

1. Walkthrough
1. Inspection
1. Informal review
1. Management approval
    <details><summary>Answer:</summary>4</details></br>

4) What statement about reviews is true?

1. Inspections are led by a trained moderator, whereas technical reviews are not necessarily.
1. Technical reviews are led by a trained leader, inspections are not.
1. In a walkthrough, the author does not attend.
1. Participants for a walkthrough always need to be thoroughly trained. 
    <details><summary>Answer:</summary>1</details></br>

5) What is the main difference between a walkthrough and an inspection?

1. An inspection is led by the authors, whilst a walk through is led by a trained moderator.
1. An inspection has a trained leader, whilst a walk through has no leader.
1. Authors are not present during inspections, whilst they are during walkthroughs.
1. A walkthrough is led by the author, whilst an inspection is led by a trained moderator. 
    <details><summary>Answer:</summary>4</details></br>

6) Which of the following characteristics and types of review processes belong together?

1. Led by the author
2. Undocumented
3. No management participation
4. Led by a trained moderator or leader
5. Uses entry and exit criteria

- (s) Inspection
- (t) Technical review
- (u) Informal review
- (v) Walkthrough

1. s = 4, t = 3, u = 2 and 5, v = 1
1. s = 4 and 5, t = 3, u = 2, v = 1
1. s = 1 and 5, t = 3, u = 2, v = 4
1. s = 5, t = 4, u = 3, v = 1 and 2 
    <details><summary>Answer:</summary>2</details></br>

7) What statement about static analysis is true?

1. With static analysis, defects can be found that are difficult to find with dynamic testing.
1. Compiling is not a form of static analysis.
1. When properly performed, static analysis makes functional testing redundant.
1. Static analysis finds all faults. 
    <details><summary>Answer:</summary>1</details></br>

8) Which of the following statements about early test design are true and which are false?

1. Defects found during early test design are more expensive to fix.
2. Early test design can find defects.
3. Early test design can cause changes to the requirements.
4. Early test design takes more effort.

1. 1 and 3 are true. 2 and 4 are false.
1. 2 is true. 1, 3 and 4 are false.
1. 2 and 3 are true. 1 and 4 are false.
1. 2, 3 and 4 are true. 1 is false. 
    <details><summary>Answer:</summary>3</details></br>

9) Static code analysis typically identifies all but one of the following problems. Which is it?

1. Unreachable code
1. Undeclared variables
1. Faults in the requirements
1. Too few comments 
    <details><summary>Answer:</summary>3</details></br>


## Chapter 4

## Chapter 5

## Chapter 6


## References:
- https://github.com/jalizadeh/ISTQB-Exam-Questions
- https://glossary.istqb.org/en_US/search?term=&exact_matches_first=true
- https://www.softwaretestinggenius.com/manual-testing/quality-systems/software-testing-skill-test/
- https://www.softwaretestinggenius.com/certifications-resources/istqb-foundation-exam-sample-question-papers/
