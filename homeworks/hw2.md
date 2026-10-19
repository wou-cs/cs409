## CS 409 - Homework 2

### Goals for this assignment
1. Implement the data layer for a pre-existing data model
2. Learn and use Entity Framework Core to effectively access the data layer from an ASP.NET Core MVC application
3. Learn and use LINQ-to-SQL to make queries on the db
4. Continue practicing all the standard and best practice MVC techniques (using Models and View-Models, writing Views and Controllers)
5. Write code that follows good design principles and is in a testable form
6. Use Dependency Injection and write and use the Repository pattern

*Note* - assumes ASP.NET / C# are chosen stack. We can discuss alternatives if necessary

### Setting

The topic for this homework is movies and tv shows.  I'm always on the lookout for interesting data sets and happened upon [this one](https://www.kaggle.com/datasets/victorsoeiro/amazon-prime-tv-shows-and-movies) at Kaggle.  The author ([Victor Soeiro.](https://github.com/victor-soeiro)) has a number of web scraping projects on GitHub.  Specifically they have scraped all the catalog information off the [JustWatch.](https://www.justwatch.com/) website service and included code to do it and data [in a repository.](https://github.com/victor-soeiro/WebScraping-Projects/tree/main/08%20-%20justwatch).  Thanks!  It includes a ton of information about tv shows and movies including who acted in them or directed.  It covers most of the major streaming services but it's so large that I decided to choose one (Amazon Prime Video) and focus on that one. 

Turns out it has the largest catalog of all so it was a good choice.  The data came in two .csv files so it wasn't in a good format for us to use in a web application.  We need it in a database.  So I wrote some Python code to read the .csv files and generate SQL.  That SQL is now in the form of up, down and seed scripts for you to use.  [They're in the class repo for you to use](https://github.com/wou-cs/cs409-hw2).

There's so much we could do with this data that this homework will just scratch the surface.  You'll use this data to make a web application that is useful for learning about movies and tv shows.

### Steps

1. **[Build the Data Layer]** We're working bottom up with this so the first thing we need to do is build the data layer.  First up, [here's the data model](https://github.com/wou-cs/cs409-hw2/blob/main/data/ER_diagram.png) I've provided for what we'll call the Streaming Database.  You'll use it without modification.

The `Show` entity includes most of the information about a tv show or movie.  Shows are tagged with `Genres`, like romance, scifi or thriller.  Each show has an identifier to say whether or not it is a tv show or movie.  `ProductionCountry` has a country identifier to say where the show was produced.  The `Person` entity is an actor or director, i.e. a person.  A `Credit` says who acted in what show and in what role.  We're using a singular naming convention for our tables and you'll need to follow this same convention throughout the class.

Here's how to build your DB. 

- Download the database script files (up, down and seed, and the dbml file for dbdiagram.io) from the repository. Create your database and run the up and seed scripts. 
- The seed script has been broken down into 3 separate files so it runs quicker: `seed_1.sql`, `seed_2.sql`, and `seed_3.sql`.  Please run them in order.
- Run some queries against it (easy if you use the [SQL plugin in VS Code](https://learn.microsoft.com/en-us/sql/tools/visual-studio-code-extensions/mssql/mssql-extension-visual-studio-code?view=sql-server-ver17))

2. **[Build an ASP.NET Core Web Application]** Create an ASP.NET Core MVC web application in your private repository within the HW2 folder.  Make sure you can build and run the starting application before proceeding.
3. **[Connect the Logic and Data Layers]** Using EF Core with the **database-first**, code based approach, connect the MVC/Business Logic Layer to the Data Layer so you can read data from the database in C#.  Here are some requirements for this step:
    - You must utilize the _repository pattern_ for accessing the db rather than accessing it directly through the `DbContext` subclass. 
    - I've given you some starting files in the class repo that include the generic repository base class and interface as well as a stubbed out `ShowRepository`.  You'll need to use these.  Please use the same folder structure as seen in class with the DAL folder.
    - You must also use _dependency injection_.
    - Double check that your model class names are singular and that the `DbSet`properties in the `DbContext` subclass are plural.  Just making sure we got the correct naming plurality.
4. **[Add a welcoming home page]** Super simple one here.  Remove what the template gives you on the home page and make a super simple welcome.  It should simply give this page a title and say something like: "Coming Soon! While you wait, check out some info about our project."
5. **[Read from the DB and build a simple feature requiring some simple and some slightly more complex LINQ queries]** Build a feature that presents some information about the data held in the Streaming Database so users can understand a little about the data available.  Do this on a separate page at `/home/info` with a link in the navbar for navigation.  This page has no user interaction -- you're just showing them this information.  You get to decide how to present this.  Please make it look somewhat nice.  (As usual, this means you must use Bootstrap for styling at a minimum.) Remember when doing this that the only computation you may perform inside a view is presentation based computation.  No business logic may go there.  And definitely no database access can go there.  You will lose points if you do so.  
    Show them or answer the following questions.  Note: these go in order of difficulty.  Do the last one last as it's the most difficult. 
    - How many shows are in the database?  How many of those are movies and how many are tv shows?
    - Which show has the highest TMDB popularity?
    - Which show has the most IMDB votes?
    - What genres are available? List them in alphabetical order.
    - What director has the most shows in the database?  Show their name and the titles of all their shows.  *Note*: some directors also star in the same movie they're directing.  This can be a complication. 
6. **[Testing]** Lastly, this homework has no computation in it that can be unit tested in a simple way.  All we are doing is retrieving information from the database and formatting it into a view for the user.  We will learn later this term how to test code that accesses a db as well as how to test JavaScript.  Therefore, you do not need to perform any testing for this homework and there is no need for a separate testing project.
7. **[Turn it in!]** Push your code to your private repository before the due date. You'll demo the work in a video meeting you'll schedule with me.

This assignment is due the weekend of November 6-8. Not a hard deadline, but I want to be able to review by the start of the following week. Stay engaged with me over email as questions come up. Chat with me on Discord or schedule time as you need help.