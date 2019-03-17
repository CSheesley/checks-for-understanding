## Week One - Module 2 Recap

Fork this respository. Answer the questions to the best of your ability. Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week (which is a TON!).

Note: When you're done, submit a PR.

### Week 1 Questions

1. List the five common HTTP verbs and what the purpose is of each verb.
- Get - READ
- Post - CREATE
- Put - all UPDATE
- Patch - partial UPDATE
- Delete - DESTROY

2. What is Sinatra?
- A DSL (Domain Specific Language) witten in Ruby, which is a Web Framework.

3. What is MVC? 
- MODEL - Data Logic -  Interacts with the database.
- VIEW - View Logic - Responsible for what the client's browser sees.
- CONTROLLER - Application Logic - Traffic Cop. Transfers data and requests to the proper places.
* Together, they create the functionality of web pages. 

4. Why do we follow conventions when creating our actions/path names in our Sinatra routes?
- This helps create RESTful routes, which are easier to understand for both the end user, and the developers who are managing a web platform.

5. What types of variables are accessible in our view templates without explicitly passing them?
- Public/Global variables, can be seen anywhere, including in views without explicitly being passed in.
* $current_time = Time.now 

6. Given the following block of code, how would I pass an instance variable `count` with a value of `1` to my `index.erb` template?

  ```ruby
  get '/horses' do
    @count = 1
    erb :index
  end
  ```
7. In the same code block, how would I pass a local variable `name` with a value of `Mr. Ed` to the view?

  ```ruby
  get '/horses' do
    render locals: { name: 'Mr. Ed'}
    erb :index
  end
  ``
  Maybe? Although I don't fully understand.

8. What's the purpose of ERB?
- ERB is a file format that allows us to use Ruby code in our view files. We use `erb` tags to deliniate what information is rendered and visible by the client, and what is simply code that is used for calcualting. <%= %>, or <% %>.

9. Why do I need a development AND test database?
- A test database is used simply for testing. The information that you provide in your model and feature tests populate this database. Each time a test is ran, the test database is cleaned - populated - checked - and then cleaned again for the next test. An acronym for this is SEAT (Setup, Exercise, Assertion, Teardown).
- Your development is used for building things on a slightly bigger scale, where you can look at rendered views of a mock version of your site. This database is not affected by testing, and it is important to keep these seperate.

10. What is CRUD and why is it important?
- CRUD is how we interact with 'rescources', which is typically anything that gets stored in a database. 
- CREATE
- READ
- UPDATE
- DESTROY
- Following this consistent and predefined framework for interacting with resources, allows you to focus your energy on the app, versus recreating a framework each time.

11. What does HTTP stand for?
- HyperText Transfer Protocol

12. What are the two ways to interpolate Ruby in an ERB view template? What's the difference between these two ways?
- 1) #{@comedian.name}
- 2) (name = ?, age = ?, @user.name, @user.age) * maybe? 

13. What's an ORM? What does it do?
- Object Relational Mapper. It allows us to interact with databases in an easier fashion. ORM's created object instances for each row in a database (where colums act as attributes). This allows us to use Ruby code to interact with these resources.

14. What's the most commonly used ORM in ruby (Sinatra & Rails)?
- Active Record

15. Let's say we have an application with restaurants. There are seven verb + path combinations necessary to provide full CRUD functionality for our restaurant application. List each of the seven combinations, and explain what each is for.
- INDEX   - get '/comedians'          display a list of all comedians
- NEW     - get '/comedians/new'      shows a form for creating new comedians
- CREATE  - post '/comedians'         add a new comedian item to the database list  - redirect
- SHOW    - get '/comedians/:id       display information for a single comedian
- EDIT    - get '/comedians/:id/edit' show a form for editing a single comedian
- UPDATE  - put '/comedians/:id       updates info for a single comedian - redirect
- DESTROY - delete '/comedians/:id    deletes a single comedian - redirect

16. What's a migration?
- A migration is action taken to populate or change a database.
- rake db: create_migration NAME=create_comedians
- rake db: create_migration NAME=add_age_column

17. When you create a migration, does it automatically modify your database?
- No, after you create a migration you are ready for this information to populate your database. However, you must first drop your current database, and then repopulate it with information from both migrations. (When you run the migration command, instructions for all of your migrations are processed).
- rake db:{drop,create,migrate}

18. How does a model relate to a database?
- The model is the part of MVC that interacts with the database and is responsible for doing the bulk of data manipulation. It is the Data Logic piece of the puzzle. All Controllers have access to all Models and their respective class methods.

19. What is the difference between `#new` and `#create`?
- Both instantiate a new object - however using #create saves the object to the database - whereas if you use #new, you will need to use a .save method to add that new object to the database.

20. Given a table named `animals`, What is the SQL query that will return all info from that table?
    `id     name        number_of_legs
    -----   ------      --------------
      1     panda       4
      2     giraffe     4
      3     whale       0
      4     bird        2
    `
- SELECT * FROM animals;

21. Using the same table, What is the SQL query that will return only the animals that has 4 legs?

- SELECT * FROM animals WHERE number_of_legs=4;

### Review Questions:  
22. Given a CSV file (“films.csv”) with these headers [id, title, description], how would you load these into your database to create new instances of Film?  

- Unsure on the CSV import.
- Would populate a seed file which would look like below
- Film.create(id: ?, title: ?, description: ?)

23. Given the following hash:
```
activities = {
  hiking: {cost: $0, supplies: ['hiking shoes', 'water', 'compass']},
  karaoke: {cost: $10, supplies: ['courage', 'microphone']},
  brunch: {cost: $35, supplies: ['mimosa flutes']},
  antiquing: {cost: $200, supplies: ['list of antique stores']}
}
```
How would I add 'granola bar' to things you should have when hiking?
activities[:hiking][:supplies] << 'granola bar'

24. What are the 4 Principles of OOP? Give a one sentence explanation of each.
- ENCAPSULATION
- ABSTRACTION
- INHERITANCE
- POLYMORPHISM 

### Self Assessment:
Choose One: (erase the others)

* I was able to answer a few questions independently, but relied heavily on outside resources

Choose One:

* I feel overwhelmed by the content presented this week

