# Getting Started

In class, you will meet with your group and brainstorm ideas for your project's topic.

Please do your best to spend the indicated amount time on each step.

Take notes on each step and submit them to Canvas at the end of the class period.

## Introductions (5 minutes)

Introduce yourselves to each other and share your interests and skills. Some ideas for conversation starters:

- What are your hobbies?
- Any early project ideas?
- What are you excited to learn more about in this class?
- What have you struggled with so far?
- Do you have any extenuating circumstances that might affect your availability to the rest of the group?

## Choose a topic domain (10 minutes)

Based on your common interests, choose a topic domain for your project based on the categories I provided on the intake survey. This decision doesn't have to be final, but will serve as a basis for the rest of your research during this period. Browse open data sets that might be relevant to your research questions to help guide your decisions. [Awesome Public Datasets](https://github.com/awesomedata/awesome-public-datasets) might be a good place to start

- Life Sciences
- Math/Physics
- Computing/Machine Learning
- Sports
- Entertainment Industry
- Economics/Finance
- Sociology/Epidemiology
- Politics/Government

## Brainstorm research questions (20 minutes)

Based on your topic domain, brainstorm a list of research questions/hypothesis that you might be interested in answering. These questions should be open-ended and not easily answered with a simple Google search. While you should make these questions, data-centric, try to focus more on broad utility of your research question than its suitability for data science. For example, a hypothesis that addresses some strategical decisions or social phenomenon would be more well-received than a hypothesis that simply asks "Can i make a predictive model for *x*?"

Start with a list of 3-5 ideas and narrow them down as you answer the following questions.

## Think about your output (20 minutes)

Think about what kind of output you want to produce for your project. This will help you narrow down your research questions and data sets. Primarily, you should think about:
- What kinds of metrics are appropriate and established for your topic domain?
- What kinds of analysis need to be performed to obtain these metrics?
- What kinds of visualizations might help consumers of your analysis understand how the data supports your conclusions?


## Design Behavior-Driven Development (BDD) requirements (20 minutes)

Based on your previous findings, design a set of BDD requirements for your project. These requirements should be written in the form of a user story, and should be specific enough to be testable.

Check out the *Cucumber* documentation on [BDD](https://cucumber.io/docs/bdd/) to learn more about the topic and view more examples and tips.

## Next Steps

If you have any time left, you may want to start delegating tasks and responsibilities to each member of your group. If possible, try to plan to work in at least pairs and schedule face to face time. Decide on a communication platform and what your expectations should be before the next in-class group work session. You do not need to include these considerations in your report.

# BDD Example

## Feature: Evaluating Educational Value of Non-traditional Education Modules

## Background

### Given
that I have a detailed record of user engagement, including video views, quiz submissions, discussion participation, and feedback forms from our platform.
And I have a trained model that measures educational metrics, such as retention rate, comprehension level, and application capability, based on user interactions and assessment results.

### Measuring comprehension level for a 'Quantum Physics' module

Given I have 2,000 users who completed the 'Quantum Physics' module on our platform over the last month
When I process their quiz scores, feedback, and engagement metrics through the educational metrics model
Then I should determine the average comprehension level for this module
And compare it with the comprehension level of traditional classroom-based teaching methods for the same topic.

### Evaluating retention rate for a 'World History' module using spaced repetition techniques

Given our 'World History' module employs spaced repetition techniques for memory enhancement
And I have six-month post-completion data from 5,000 users who took this module
When I process this data through the educational metrics model
Then I should determine the long-term retention rate of historical facts by these users
And contrast this with retention rates from traditional memorization methods.

### Assessing application capability from a 'Practical Geometry' module

Given I have data from 1,000 users who took our 'Practical Geometry' module and subsequently participated in a project-based assessment
When I evaluate their project outcomes and feedback through the educational metrics model
Then I should gauge their capability to apply theoretical geometry knowledge in practical scenarios
And juxtapose this capability with students who learned geometry through traditional textbook methods.

### Highlighting the value proposition for stakeholders

Given I have comprehensive educational metrics for multiple modules on our platform
When I compile a report contrasting our results with traditional education benchmarks
Then I should be able to present a clear value proposition to stakeholders, showcasing areas where our platform excels
And areas where we aim to further enhance our methodologies based on the data-driven insights.

### Crafting data-backed advertising campaigns

Given the scientifically tested educational metrics that showcase our platform's strengths
When I liaise with the marketing team to craft advertising campaigns
Then the campaigns should prominently feature these strengths, giving potential users a quantifiable understanding of our platform's value.
