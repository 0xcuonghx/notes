The Solidity assert() function is meant to assert invariants. Properly functioning code should never reach a failing assert statement. A reachable assertion can mean one of two things:

1. A bug exists in the contract that allows it to enter an invalid state;
2. The assert statement is used incorrectly, e.g. to validate inputs.
