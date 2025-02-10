# Table of Contents
- [Table of Contents](#table-of-contents)
  - [Exam Set 1](#exam-set-1)
  - [References:](#references)

---

## Exam Set 1

1) If a program is tested and 100% branch coverage is achieved, which of the following coverage criteria is then guaranteed to be achieved?
1. 100% Equivalence class coverage
1. 100% Condition coverage and 100% Statement coverage
1. 100% Statement coverage
1. 100% Multiple condition coverage
    <details><summary>Answer:</summary>2</details></br>

2) This part of a program is given:
```
WHILE (condition A)
Do B
END WHILE
```
How many decisions should be tested in this code in order to achieve 100% decision coverage? 
1. 2
1. Indefinite
1. 1
1. 4
    <details><summary>Answer:</summary>2</details></br>

3) In a flight reservation system, the number of available seats in each plane model is an input. A plane may have any positive number of available seats, up to the given capacity of the plane. Using Boundary Value analysis, a list of available – seat values were generated. Which of the following lists is correct?

1. 1, 2, capacity -1, capacity, capacity plus 1
1. 0, 1, capacity, capacity plus 1
1. 0, 1, 2, capacity plus 1, a very large number
1. 0, 1, 10, 100, capacity, capacity plus one
    <details><summary>Answer:</summary>2</details></br>

4) Which of the following is a valid collection of equivalence classes for the following problem: An integer field shall contain values from and including 1 to and including 15
1. Less than 1, 1 through 15, more than 15
1. Negative numbers, 1 through 15, above 15
1. Less than 1, 1 through 14, more than 15
1. Less than 0, 1 through 14, 15 and more
    <details><summary>Answer:</summary>1</details></br>

5) This part of a program is given:
```
WHILE (condition A) Do B END WHILE
```
How many paths should be tested in this code in order to achieve 100% path coverage?
1. 1
1. Indefinite
1. 2
1. 4
    <details><summary>Answer:</summary>3</details></br>

6) If a program is tested and 100% condition coverage is achieved, which of the following coverage criteria is then guaranteed to be achieved?
1. 100% branch coverage
1. 100% condition coverage and 100% statement coverage
1. Equivalence class and boundary value coverage
1. No other white box coverage criterion is guaranteed to be fulfilled 100%
    <details><summary>Answer:</summary>2</details></br>

7) Branch Coverage
1. Another name for decision coverage
1. Another name for all-edges coverage
1. Another name for basic path coverage
1. All the above
    <details><summary>Answer:</summary>4</details></br>

8) A test case design technique for a component in which test cases are designed to execute statements is called as?
1. State transition Testing
1. Static Testing
1. Transition testing
1. Statement testing
    <details><summary>Answer:</summary>4</details></br>

9) if (condition1 && (condition2 function1())) statement1; else statement2;
1. Decision coverage
1. Condition coverage
1. Statement coverage
1. Path Coverage
    <details><summary>Answer:</summary>2</details></br>

10) In _____ testing test cases i.e input to the software are created based on the specifications languages
1. State Transition Testing
1. Random Testing
1. Syntax Testing
1. Penetration testing
    <details><summary>Answer:</summary>3</details></br>

11) White Box Testing
1. Same as glass box testing
1. Same as clear box testing
1. Both A and B
1. None of the above
    <details><summary>Answer:</summary>3</details></br>

12) Equivalence partitioning consists of various activities:
1. Ensure that test cases test each input and output equivalence class at least once
1. Identify all inputs and all outputs
1. Identify equivalence classes for each input
1. All of the above 
    <details><summary>Answer:</summary>4</details></br>

13) Structural Testing
    1. Same as black box testing
    1. Same as white box testing
    1. Same as functional testing
    1. None of the above.
    <details><summary>Answer:</summary>2</details></br>

14) Path coverage includes
1. Statement coverage
1. Condition coverage
1. Decision coverage
1. None of these
    <details><summary>Answer:</summary>4</details></br>

15) Which testing technique do you prefer for the following situations?
    - (A) Severe time pressure
    - (B) Inadequate specification

1. Decision testing
1. Error guessing
1. Statement testing
1. Exploratory testing
    <details><summary>Answer:</summary>4</details></br>

16) Recovery testing is a system test that forces the software to fail and verifies that data recovery is properly performed. The following should be checked for correctness
    - (A) Re-initialization
    - (B) Restart
    - (C) Data Recovery
    - (D) Check Point Mechanism

1. A and B
1. A, B and C
1. A, B, C and D
1. B and D
    <details><summary>Answer:</summary>3</details></br>

17) Data flow analysis studies:
1. Possible communications bottlenecks in a program
1. The rate of change of data values as a program executes
1. The use of data on paths through the code
1. The intrinsic complexity of the code
    <details><summary>Answer:</summary>3</details></br>


18) Which of the following is NOT a white box technique?
1. Statement testing
1. Path testing
1. Data flow testing
1. State transition testing
    <details><summary>Answer:</summary>4</details></br>

19) Which of the following statements is NOT correct?
1. A minimal test set that achieves 100% LCSAJ coverage will also achieve 100% branch coverage
1. A minimal test set that achieves 100% path coverage will also achieve 100% statement coverage
1. A minimal test set that achieves 100% path coverage will generally detect more faults than one that achieves 100% statement coverage
1. A minimal test set that achieves 100% statement coverage will generally detect more faults than one that achieves 100% branch coverage
    <details><summary>Answer:</summary>4</details></br>

20) Error guessing:
1. Supplements formal test design techniques
1. Can only be used in component, integration and system testing
1. Is only performed in user acceptance testing
1. Is not repeatable and should not be used
    <details><summary>Answer:</summary>1</details></br>

21) In a system designed to work out the tax to be paid:
```
An employee has £4000 of salary tax free. The next £1500 is taxed at 10% The next £28000 is taxed at 22%
Any further amount is taxed at 40% Which of these groups of numbers would fall into the same equivalence class?
```
1. £4800; £14000; £28000
1. £5200; £5500; £28000
1. £28001; £32000; £35000
1. £5800; £28000; £32000
    <details><summary>Answer:</summary>4</details></br>

22) In a system designed to work out the tax to be paid:
```
An employee has £4000 of salary tax free. The next £1500 is taxed at 10% The next £28000 is taxed at 22%
Any further amount is taxed at 40%
```
To the nearest whole pound, which of these is a valid Boundary Value Analysis test case?
1. £1500
1. £32001
1. £33501
1. £28000
    <details><summary>Answer:</summary>3</details></br>

23) Which of the following is NOT true of test coverage criteria?
1. Test coverage criteria can be measured in terms of items exercised by a test suite
1. A measure of test coverage criteria is the percentage of user requirements covered
1. A measure of test coverage criteria is the percentage of faults found
1. Test coverage criteria are often used when specifying test completion criteria
    <details><summary>Answer:</summary>3</details></br>

24) Analyze the following highly simplified procedure:
```
1. Ask: "What type of ticket do you require, single or return?" 
2. IF the customer wants ‘return’ 
3. Ask: "What rate, Standard or Cheap-day?" 
4. IF the customer replies ‘Cheap-day’ 
5. Say: "That will be £11:20" 
6. ELSE 
7. Say: "That will be £19:50" 
8. ENDIF 
9. ELSE 
10. Say: "That will be £9:75" 
11. ENDIF
```
Now decide the minimum number of tests that are needed to ensure that all the questions have been asked, all combinations have occurred and all replies given.
1. 3
1. 4
1. 5
1. 6
    <details><summary>Answer:</summary>1</details></br>

25) Given the following specification, which of the following values for age are in the SAME equivalence partition?
```
If you are less than 18, you are too young to be insured. Between 18 and 30 inclusive, you will receive a 20% discount. Anyone over 30 is not eligible for a discount.
```
1. 17, 18, 19
1. 29, 30, 31
1. 18, 29, 30
1. 17, 29, 31
    <details><summary>Answer:</summary>3</details></br>

26) Consider the following statements:
    - (A) 100% statement coverage guarantees 100% branch coverage
    - (B) 100% branch coverage guarantees 100% statement coverage
    - (C) 100% branch coverage guarantees 100% decision coverage
    - (D) 100% decision coverage guarantees 100% branch coverage
    - (E) 100% statement coverage guarantees 100% decision coverage

1. B is True; A, C, D & E are False
1. A & E are True; B, C & D are False
1. B & C are True; A, D & E are False
1. B, C & D are True; A & E are False
    <details><summary>Answer:</summary>4</details></br>

27) In a system designed to work out the tax to be paid:
```
An employee has £4000 of salary tax free. The next £1500 is taxed at 10%. The next £28000 after that is taxed at 22%. Any further amount is taxed at 40%.
```
To the nearest whole pound, which of these is a valid Boundary Value Analysis test case?
1. £28000
1. £33501
1. £32001
1. £1500
    <details><summary>Answer:</summary>2</details></br>

28) Considering the following pseudo-code, calculate the MINIMUM number of test cases for statement coverage, and the MINIMUM number of test cases for decision coverage respectively.
```
READ A 
READ B 
READ C 
IF C>A THEN 
IF C>B THEN 
PRINT "C must be smaller than at least one number" 
ELSE 
PRINT "Proceed to next stage" 
ENDIF 
ELSE 
PRINT "B can be smaller than C" 
ENDIF
```
1. 3, 3
1. 2, 3
1. 2, 4
1. 3, 2
    <details><summary>Answer:</summary>1</details></br>

29) The following statements are used to describe the basis for creating test cases using either black or white box techniques:

    - (A) Information about how the software is constructed.
    - (B) Models of the system, software or components.
    - (C) Analysis of the test basis documentation.
    - (D) Analysis of the internal structure of the components.

Which combination of the statements describes the basis for black box techniques?

1. B and C
1. B and D
1. A and D
1. A and C
    <details><summary>Answer:</summary>1</details></br>

30) Consider the following techniques. Which are static and which are dynamic techniques?
    - (A) Equivalence Partitioning
    - (B) Use Case Testing
    - (C) Data Flow Analysis
    - (D) Exploratory Testing
    - (E) Decision Testing
    - (F) Inspections

1. A-D are static, E-F are dynamic
1. C and F are static, A, B, D and E are dynamic
1. B, C and F are static, A, D and E are dynamic
1. F is static, A-E are dynamic
    <details><summary>Answer:</summary>2</details></br>

31) Given the following code, which statement is true about the minimum number of test cases required for full statement and branch coverage?
```
Read p 
Read q 
IF p+q > 100 THEN 
Print "Large" 
ENDIF 
IF p > 50 THEN 
Print "p Large" 
ENDIF
```
1. 1 test for statement coverage, 3 for branch coverage
1. 1 test for statement coverage, 2 for branch coverage
1. 1 test for statement coverage, 1 for branch coverage
1. 2 tests for statement coverage, 2 for branch coverage
    <details><summary>Answer:</summary>2</details></br>

32) In a system designed to work out the tax to be paid:
```
An employee has £4000 of salary tax free. 
The next £1500 is taxed at 10%. 
The next £28000 after that is taxed at 22%. 
Any further amount is taxed at 40%.
```
To the nearest whole pound, which of these groups of numbers fall into three DIFFERENT equivalence classes?

1. £4000; £5000; £5500
1. £32001; £34000; £36500
1. £28000; £28001; £32001
1. £4000; £4200; £5600
    <details><summary>Answer:</summary>3</details></br>

33) Which of the following statements about component testing is FALSE?
1. Black box test design techniques all have an associated test measurement technique
1. White box test design techniques all have an associated test measurement technique
1. Cyclomatic complexity is not a test measurement technique
1. Black box test measurement techniques all have an associated test design technique
    <details><summary>Answer:</summary>1</details></br>

34) When testing a grade calculation system, a tester determines that all scores from 90 to 100 will yield a grade of A, but scores below 90 will not. This analysis is known as:
1. Equivalence partitioning
1. Boundary value analysis
1. Decision table
1. Hybrid analysis
    <details><summary>Answer:</summary>1</details></br>

35) Which technique can be used to achieve input and output coverage? It can be applied to human input, input via interfaces to a system, or interface parameters in integration testing.
1. Error Guessing
1. Boundary Value Analysis
1. Decision Table testing
1. Equivalence partitioning
    <details><summary>Answer:</summary>4</details></br>

36) Which of the following statements is true about white-box testing?
1. It includes functional testing
1. It includes loop testing
1. It is usually done after black-box testing
1. It is usually done during the integration testing phase
    <details><summary>Answer:</summary>2</details></br>

37) What is a key characteristic of structure-based testing techniques?
1. They are mainly used to assess the structure of a specification
1. They are used both to measure coverage and to design tests to increase coverage
1. They are based on the skills and experience of the tester
1. They use a formal or informal model of the software or component
    <details><summary>Answer:</summary>2</details></br>

38) Which of the following would be an example of decision-table testing for a financial application applied at the system-test level?
1. A table containing rules for combinations of inputs to two fields on a screen
1. A table containing rules for interfaces between components
1. A table containing rules for mortgage applications
1. A table containing rules for chess
    <details><summary>Answer:</summary>3</details></br>

39) Which of the following could be a coverage measure for state transition testing?
    - (V) All states have been reached.
    - (W) The response time for each transaction is adequate.
    - (X) Every transition has been exercised.
    - (Y) All boundaries have been exercised.
    - (Z) Specific sequences of transitions have been exercised.

1. X, Y and Z
1. V, X, Y and Z
1. W,X and Y
1. V, X and Z
    <details><summary>Answer:</summary>4</details></br>

40) Postal rates for 'light letters' are 25p up to 10g, 35p up to 50g plus an extra 10p for each additional 25g up to 100g.   
Which test inputs (in grams) would be selected using equivalence partitioning?

1. 8, 42, 82, 102
1. 4, 15, 65, 92, 159
1. 10, 50, 75, 100
1. 5, 20, 40, 60, 80
    <details><summary>Answer:</summary>2</details></br>
---

## References:
- https://github.com/jalizadeh/ISTQB-Exam-Questions
- https://www.softwaretestinggenius.com/manual-testing/quality-systems/software-testing-skill-test/
- https://www.softwaretestinggenius.com/certifications-resources/istqb-foundation-exam-sample-question-papers/
