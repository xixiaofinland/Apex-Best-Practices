
# Apex Testing Recommendations

## Naming of The Test Class

Follow the naming convention of existing Apex test classes in the org. Usually, it is the same class name with `Test` prefix or suffix.

## Naming of the Test Function

The name of test function should reveal its purpose, for example `addThreeAndFourShouldEqualToSeven()`, or `runWithoutAccountValueShouldNotInsertRecord()`

## Scenarios of the Test Function

It is recommended to cover at least one "happy path" scenario and one "sad path" scenario.

## Use @testSetup

The commonly used data setup steps must be added into the data setup method with `@testSetup` annotation.

## Use Test.startTest() and Test.stopTest()

These 2 methods are used to reset the governor limits within the context of your test execution and to be able to test asynchronous methods.

It is recommended to use them in all test methods, as they serve as boundaries of data setup, test execution, and test result validation.

## Hide Unnecessary Details

Do not put all nitty gritty into one test function. Hide details into private functions for readers.

```
@isTest
public static void addThreeAndFourShouldEqualToSeven(){
	setupSomeData();
	Test.StartTest();
	ExecuteSomeCode();
	Test.StopTest();
	//Do asserts here;
}
```

## Unified Test Data Generation

Define the project or org level way to generate test data. For instance, how to create test users, test accounts etc.
Once it is defined, stick to the same method across the entire project or org.

## Unit Test Quality

Treat unit test as important as production code.
If Test Driven Development model is not used, create and improve unit tests along with production code evolvement. It is too late to write unit tests when production code is already finished.



# Other points:

CSV files for testing data (8:30)
- ID can be in CSV
- bulk test (easy to add data into csv)
- CSV way cannot load data into memory

Mocking
- httpCallOut

System.StubProvider

Avoid DML (35:24)

## Reference:
[Advanced Apex Testing](https://www.youtube.com/watch?v=IWVpaYBx3bc)
