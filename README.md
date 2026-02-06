# CHIP 5.3: Rails Intro - RottenPotatoes (Movies CRUD)

This homework introduces the Rails MVC flow by building a simple RottenPotatoes-style app.
You will complete and verify a basic Movies CRUD interface with Rails conventions.

**NOTE: If you are working on a local computer, do not clone this repo to your workspace. Fork it first, then clone your fork.**

Notice
--------------
Make sure the ruby version is set to 3.3.8 in your Gemfile:

```rb
source 'https://rubygems.org'
ruby '3.3.8'
```

Learning Goals
--------------
After completing this assignment, you will be able to:

* Understand the Rails MVC workflow for a resource
* Implement standard RESTful CRUD actions and views
* Run Rails tests and interpret failures
* Work with Rails fixtures and seeded data

Overview
--------

The app already includes a Movie model and migration with these fields:

* title (string)
* rating (string)
* description (text)
* release_date (datetime)

Routes are set up with `resources :movies`, and the root path redirects to `/movies`.
You will complete the UI and tests for the Movies resource.

Where to Work
-------------

Primary files you will touch:

* `app/views/movies/index.html.erb` (Part 2 starts here)
* `app/views/movies/_form.html.erb`, `app/views/movies/show.html.erb`, `app/views/movies/edit.html.erb`, `app/views/movies/new.html.erb`
* `test/controllers/movies_controller_test.rb`
* `test/system/movies_test.rb`
* `test/fixtures/movies.yml` (you need to add this file)

Tasks
-----

1. Complete the Movies index page starting at the `Part 2: Start here...` marker.
2. Add rating filters (checkboxes) and sorting (dropdown) on the index page.
3. Keep the selected ratings and sort option after submitting and after reload.
4. Ensure the Movies CRUD flow works end-to-end: index, show, new, create, edit, update, destroy.
5. Add fixtures in `test/fixtures/movies.yml` so tests using `movies(:one)` pass.
6. Run the tests and fix any failures.

Local Setup (Optional)
----------------------

Install gems and set up the database:

```sh
bundle install
bin/rails db:create db:migrate db:seed
```

Run the app:

```sh
bin/rails server
```

Visit `http://localhost:3000/movies` to manually verify:

* Filtering by ratings changes the list
* Sorting by Title and Release date works
* Your selections persist after submitting and refreshing

Tests
-----

Run all tests:

```sh
bin/rails test
```

Run only the movies controller tests:

```sh
bin/rails test test/controllers/movies_controller_test.rb
```

Run only the system tests:

```sh
bin/rails test test/system/movies_test.rb
```

Notes
-----

* The test suite expects fixtures to exist under `test/fixtures/*.yml`.
* Seed data in `db/seeds.rb` is for manual testing only; it does not replace fixtures.

Pre-submission Checklist
------------------------

Before you push, make sure all of the following work in your local app:

* The Movies index loads and lists movies
* Rating checkboxes filter the list correctly
* Sorting by Title and Release date works
* Selected ratings and sort choice persist after submit and reload
* You can create, edit, and delete a movie via the UI
* `bin/rails test` passes

GitHub Actions Autograding
--------------------------

Each push triggers GitHub Actions to run the autograder in CI. It will:

* boot the app in test mode
* run automated checks against the running app

If your CI run fails, open the Actions tab to view logs and download the `autograder-results` artifact.

Submission
----------

Push your changes to your assignment repository and submit according to your course instructions.
