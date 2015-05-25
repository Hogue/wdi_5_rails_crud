![General Assembly Logo](http://i.imgur.com/ke8USTq.png)

# An Introduction to ActiveRecord

## Objectives

By the end of this lesson, students should be able to:

- Create a database table using Ruby on Rails
- Insert a row or rows into a database table using ActiveRecord
- Retrieve a row or rows from a database table using ActiveRecord
- Update a row or rows in a database table using ActiveRecord
- Delete a row or rows from a database table using ActiveRecord

## Prerequisites

- [An Introduction to relational databases](https://github.com/ga-wdi-boston/wdi_5_sql_crud)
- A working [Rails](http://rubyonrails.org/download/) installation.
- Required reading: http://www.postgresql.org/docs/9.4/static/tutorial.html (please skip _3. Advanced Features_), http://guides.rubyonrails.org/v4.2.0/active_record_basics.html

## Introduction

**[ActiveRecord](http://api.rubyonrails.org/files/activerecord/README_rdoc.html)** _(see also [Active record pattern](http://en.wikipedia.org/wiki/Active_record_pattern))_ is the mechanism Rails uses to store and retrieve data from an RDBMS.  This, and similar mechanism, are referred to as an [Object-relational mapping](http://en.wikipedia.org/wiki/Object-relational_mapping) or ORM.

Why is this important?

Because the vast majority of enterprise data is stored in relational databases, but objects are often used to manipulate that data in applications. And, although **[NoSQL](http://en.wikipedia.org/wiki/NoSQL)** databases _(e.g Firebase)_ have been growing in popularity, their ability to support distributed data to enhance performance makes achieving **[ACID](http://en.wikipedia.org/wiki/ACID)** transaction a significant challenge.

**[Mongo DB Is Web Scale](https://www.youtube.com/watch?v=b2F-DItXtZs)**

The point of the video is not to state a preference for one technology over another, but to make clear that the need should drive the technology choice, not the hype.

ActiveRecord makes it easy for us to store and retrieve rows from a table

What about more complicated data?

ActiveRecord makes it easy to create objects that reference other objects (using tables that reference other tables) which allows arbitrary nesting of objects.  This is something we'll be looking at more closely later.

## Instructions

Fork and clone this repository, then

```bash
$ gem install pry-rails
$ cd wdi_4_rails_crud
$ subl .
```

We'll be using [PostgreSQL](http://www.postgresql.org/) as the [RDBMS](http://en.wikipedia.org/wiki/Relational_database_management_system) backing ActiveRecord.

The Rails App we'll be using was created with the command `rails new --database=postgresql --skip-bundle --skip-sprockets --skip-spring --skip-javascript --skip-turbolinks --skip-test-unit rails_crud`.

## Demonstration

We'll use `rails_crud_development` as the database to hold our tables and **[rails dbconsole](http://guides.rubyonrails.org/command_line.html#rails-dbconsole)** _(alias `rails db`)_ to interact with it with SQL.  By default, each Rails App is created to potentially use one of three databases, `<rails app name>_development`, `<rails app name>_test`, and `<rails app name>_production`.  We'll use **[rails console](http://guides.rubyonrails.org/command_line.html#rails-console)** _(alias `rails c`)_ to interactively use Models and **[rails runner](http://guides.rubyonrails.org/command_line.html#rails-runner)** _(alias `rails r`)_ to invoke any scripts we write.

```bash
$ cd rails_crud
$ rails db
psql: FATAL:  database "rails_crud_development" does not exist
$
```

As we can see, `rails db` runs `psql`.  If the Rails App had been configured for a different database server, `rails db` would have started a different command line client.

As before, we need to create the database.  We'll use the command line application **[rake](http://guides.rubyonrails.org/command_line.html#rake)** which Rails uses to manage changes to the structure of the database.

```bash
$ rake db:create
$
```

Rake is a task runner and `rake -T ` provide a brief description the tasks it's configured to run from the current `Rakefile`.  Let's have a look at the `db` tasks.

```bash
$ rake -T db
$
```

### Pets

We'll store and manipulate information about pets.

### Create a table

`rails generate model` _(alias `rails g model`)_

`rake db:migrate`

---

#### Insert a row

```bash
$ rails c
Loading development environment (Rails 4.2.1)
[1] pry(main)>
```

Pet.new or Pet.create

---

#### Find a row

Pet.find

---

### Modify a table

`rails generate migration` _(alias `rails g migration`)_ followed by `rake db:migrate`


---

#### Update a row

pet.update

#### Delete a row

pet.delete

Pet.delete_all

---

## Code Along

We'll repeat the above for people instead of pets.

## Lab

One more time, but for places.

Remember to keep it to data that can be stored in a single row.

