## CS 409 - Homework 1

For this assignment you'll build a simple web application that lets us solve a common problem that arises during this class: find a meeting time that works for a group of people.  Yes, we often use a Doodle poll or When2Meet for this task, but what if everyone is in the room at the same time and you just need something quick and handy to determine and visualize possible meeting times?

> The application should take in a string that identifies all the days and times people are busy and also whether or not weekends should be used as possible times to meet.  It then finds all the times where people are not busy and shows them in an easy to read, graphical way.

[Optional video to watch](https://www.youtube.com/watch?v=OKgihjOfJUg).

Other requirements:
1. Share with me via email your technical stack plans. A technical stack are the run-time programmable components: core language used for application logic, web application layer, and (if needed) the data persistence layer. You will not need a database for this assignent.
2. Use a POST request to send the busy times and weekends flag to the server.  Calculating the free times must be done on the server in the chosen application server language (**not** in Javascript in the browser).
3. After the user enters in all the busy times, chooses to include weekends or not, and submits the info, your application should determine all the free times and display them graphically in a table.  Highlight or otherwise make it easy to distinguish between times that are free and those that are busy.  I don't expect you to use JavaScript for this task.
4. You must write, and pass, 6 different unit test methods that test some part of the functional requirements of this assignment.  These tests must include real, meaningful tests of the parts of your code that takes the input, computes and returns the resulting schedule.  Six tests gives you plenty of opportunity to test edge cases (e.g. what happens if the input is invalid or just an empty string?) as well as expected correct behavior.
5. Use git and GitHub. [Invite me](https://github.com/brookscl) as a collaborator on any repos you create for this class.
6. You can use AI to help answer questions on your application, but do not use AI to create any code directly for you. Another way to put this: don't use Claude Code or ChatGPT in your solution working directory directly. In fact, don't give AI direct access to your code. It is OK to ask AI questions like "guide me through doing form validation using Python and Flask." The key: use AI to help you learn at this stage, not to build the solution. We will focus on using AI in other modes later in the school year.
7. This assignment is due the weekend of October 16-18. Not a hard deadline, but I want to be able to review by the start of the following week. Stay engaged with me over email as questions come up. We will chat in early October to clarify any questions you have.