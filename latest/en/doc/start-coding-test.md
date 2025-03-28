# Start coding from test

When a manager comes to me, I don’t ask him, “What’s the problem?” I say, “Tell me the story.”

## TDD and BDD

### Test Driven Development (TDD)
TDD is software development approach in which test cases are developed to specify and validate what the code will do. In simple terms, test cases for each functionality are created and tested first and if the test fails then the new code is written in order to pass the test and making code simple and bug-free.

![](https://miro.medium.com/max/1024/1*749GtQGqamkOqfOe40o_Tg.png)
![](https://www.guru99.com/images/8-2016/081216_0811_TestDrivenD1.png)

```php
public function testConvertDailyDatesToPeriodRange()
{
//First case
$firstDataHashList = [121, 122, 123, 125, 126, 127, 129, 130];
$expectedFirstResultDataHash[121] = ['start' => 121, 'end' => 123];
$expectedFirstResultDataHash[125] = ['start' => 125, 'end' => 127];
$expectedFirstResultDataHash[129] = ['start' => 129, 'end' => 130];

        $this->assertEquals(
            $expectedFirstResultDataHash,
            DateHelper::convertDailyDatesToPeriodRange($firstDataHashList),
            ''
        );

        //Second case
        $secondDataHashList = [121, 122, 123, 124, 125, 126, 127, 128, 129, 130];
        $expectedSecondResultDataHash[121] = ['start' => 121, 'end' => 130];

        $this->assertEquals(
            $expectedSecondResultDataHash,
            DateHelper::convertDailyDatesToPeriodRange($secondDataHashList),
            ''
        );
    }
```


### Behavior Driven Development (BDD)

BDD is a Test-First, Agile Testing practice that provides Built-In Quality by defining (and potentially automating) tests before, or as part of, specifying system behavior. BDD is a collaborative process that creates a shared understanding of requirements between the business and the Agile Teams.

![](https://www.scaledagileframework.com/wp-content/uploads/2018/09/Behavior-Driven-Development_F03_web.png)

Gherkin language, Given, When, Then :

```
Feature: Guess the word

  Background:
    Given a global administrator named "Greg"
    And a blog named "Greg's anti-tax rants"
    And a customer named "Dr. Bill"
    And a blog named "Expensive Therapy" owned by "Dr. Bill"

  # The first example has two steps
  Scenario: Maker starts a game
    When the Maker starts a game
    Then the Maker waits for a Breaker to join
    Examples:
    | start | eat | left |
    |    12 |   5 |    7 |
    |    20 |   5 |   15 |

  # The second example has three steps
  Rule: There can be only One
  @acceptancecriteria @specs @returnpolicy @nominalcase @keyexample
  Scenario: Breaker joins a game
    Given the Maker has started a game with the word "silky"
    When the Breaker joins the Maker's game
    Then the Breaker must guess a word with 5 characters
```

Tools :
- http://gist.asciidoctor.org/?github-rmpestano/cukedoctor//README.adoc&numbered&doctype=book&no-header-footer

## Border Area test

### Tools for mocking

- Mock a database : http://hsqldb.org/
- Mock a server Http : https://wiremock.org/#open-source-get-started
- Run docker container from Test file : https://www.testcontainers.org/

### Manage external service
**Contract testing** is a technique for testing an integration point by checking each application in isolation to ensure the messages it sends or receives conform to a shared understanding that is documented in a "contract".

For applications that communicate via HTTP, these "messages" would be the HTTP request and response, and for an application that used queues, this would be the message that goes on the queue.

In practice, a common way of implementing contract tests (and the way Pact does it) is to check that all the calls to your test doubles return the same results as a call to the real application would.

![](https://docs.pact.io/img/how-pact-works/summary.png)

Read the doc : https://docs.pact.io/5-minute-getting-started-guide

## Other test

### Performance testing
Performance testing is an umbrella term for both load and stress testing. Performance testing refers to all testing related to verifying the system’s performance and monitoring how it behaves under stress.
Therefore we can say that performance testing is concerned with the following metrics:
- Reliability: Determine the error rate and how it changes under higher loads.
- Stability: You can measure this through memory and CPU usage.
- Response time: Measure the average response time for requests.
- Scalability: Determine how the application behaves under different types of loads.

![](https://www.guru99.com/images/performance_testing_process.png)

Tools : https://gatling.io/

### Mutation testing
Mutation Testing is a type of software testing in which certain statements of the source code are changed/mutated to check if the test cases are able to find errors in source code. The goal of Mutation Testing is ensuring the quality of test cases in terms of robustness that it should fail the mutated source code.

![](https://www.guru99.com/images/m2.png)

### Chaos testing
Limit between dev and devops.
Netflix have a great library, you can take a look, https://netflix.github.io/chaosmonkey/

![](https://netflix.github.io/chaosmonkey/logo.png)
