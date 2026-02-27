[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/2xoNp9W2)
[![Open in Codespaces](https://classroom.github.com/assets/launch-codespace-2972f46106e565e64193e422d61a12cf1da4916b45550586e14ef0a7c637dd04.svg)](https://classroom.github.com/open-in-codespaces?assignment_repo_id=22893990)
# Rails Intro - RottenPotatoes (Movies CRUD)

This homework introduces the Rails MVC flow by building a simple RottenPotatoes-style app.
You will complete and verify a basic Movies CRUD interface with Rails conventions.

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

Primary files you will touch (files requiring modifications to complete the assignment are not limited to the following):

* `app/views/movies/index.html.erb` (Part 2 starts here)
* `app/views/movies/_form.html.erb`, `app/views/movies/show.html.erb`, `app/views/movies/edit.html.erb`, `app/views/movies/new.html.erb`
* `test/controllers/movies_controller_test.rb`
* `test/system/movies_test.rb`
* `test/fixtures/movies.yml` (you need this file for local testing)

Tasks
-----

1. Complete the Movies index page starting at the `Part 2: Start here...` marker.
2. Add rating filters (checkboxes) and sorting (dropdown) on the index page.
3. Keep the selected ratings and sort option after submitting and after reload.
4. Ensure the Movies CRUD flow works end-to-end: index, show, new, create, edit, update, destroy.
5. Run the tests and fix any failures.

Local Setup
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

- `bin/rails test` passes (Passing the test here does not mean the completion of the assignment. Please also use the server to check whether the following functions which will be tested by autograder have been implemented.)
- **App responds:** Visiting the app (on `localhost:3000`) returns a normal page without errors.
- **Ratings form exists:** The movies page includes a filter `<form>` with `id="ratings_form"`.
- **Submit button exists:** The filter form includes a submit control with `id="ratings_submit"`.
- **Rating checkboxes exist:** The filter form includes checkboxes for the available movie ratings (e.g., G/PG/PG-13/R). Each checkbox `id` must follow the pattern `ratings_X` (e.g., `ratings_G`, `ratings_PG`, `ratings_PG-13`, `ratings_R`).
- **Uniform defaults:** On first load, the rating checkboxes are either all checked or all unchecked (not mixed).
- **Filter by rating works:** Submitting selected ratings shows only movies whose ratings are selected. Each movie should be rendered inside `<div id="movies">` as `<div id="movie_<id>">`, containing `<p><strong>Title:</strong> ...</p>`, `<p><strong>Rating:</strong> ...</p>`, and `<p><strong>Release date:</strong> ...</p>`.
- **Filter state persists:** After submitting the filter, the same ratings remain checked on the reloaded page.
- **Sort by Title works:** The form includes a dropdown (`<select>`) with `name="sort_by"`. The dropdown must have an option with text `"Title"` and value `"title"`. Selecting it and submitting sorts movies alphabetically by title.
- **Sort by Release Date works:** The dropdown must have an option with text `"Release date"` (case-insensitive match on "Release date") and value `"release_date"`. Selecting it and submitting sorts movies chronologically.
- **Filters persist during sorting:** Changing the sort order does not clear the selected rating filters.
- **Sort remembered on reload:** Reloading the page keeps the currently selected sort order (and the dropdown reflects it). The `sort_by` field value should remain `"title"` or `"release_date"` after reload.
- **RESTful redirect:** Filtering/sorting results in a RESTful URL with query parameters (e.g., `?sort_by=release_date&ratings[PG]=1`) rather than staying on a non-RESTful submission URL. Note: rating parameters should use the `ratings[X]` format (e.g., `ratings[PG]`, `ratings[R]`).
- **RESTful restores ratings:** Reloading a RESTful URL restores the rating filters (movies shown + checkboxes).
- **RESTful restores sort:** Reloading a RESTful URL restores the sort order (movie order + dropdown selection).

You can find more details about the test in `.github/workflows/classroom.yml` to help you complete the assignment.

GitHub Actions Autograding
--------------------------

Each push triggers GitHub Actions to run the autograder in CI. It will:

* boot the app in test mode
* run automated checks against the running app

If your CI run fails, open the Actions tab to view logs and download the `Autograding Reporter` artifact.

