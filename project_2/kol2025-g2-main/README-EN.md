# Exam task

It is required to develop a web application for managing ski slopes.

## Functional requirements

- **(20 points)** On the routes `/` and `/ski-slopes`, you need to display a list of all created ski slopes using the
  `list.html` template. Additionally, pagination of the ski slopes must be enabled.
    - The implementation of this functionality can be verified with the tests `test_list_10pt` and
      `test_pagination_10pt`.

- **(20 points)** It is required to implement adding a new ski slope. When clicking the Add new ski slope button from
  the
  `list.html` template, the `form.html` template should be displayed at the route `/ski-slopes/add`, where upon clicking
  **Submit**, a new ski slope is created and saved in the database. After that, the page `/ski-slopes` should be
  displayed.
    - The implementation of this functionality can be verified with the tests `test_create_10pt` and
      `test_create_mvc_10pt`.

- **(5 points)** It is required to implement deletion of a ski slope. When clicking the **Delete** button from the
  `list.html`
  template, the ski slope should be deleted from the database. After that, the page `/ski-slopes` should be displayed.
    - The implementation of this functionality can be verified with the tests `test_delete_3pt` and
      `test_delete_mvc_2pt`.

- **(20 points)** It is required to implement editing the details of a ski slope. When clicking the **Edit** button from
  the `list.html` template, the `form.html` template should be displayed at the route `/ski-slopes/edit/[id]`, where
  the `<input>` elements will contain the current values of the ski slope being edited. Upon clicking **Submit**,
  the changes to the ski slope should be saved in the database. After that, the page `/ski-slopes` should be displayed.
    - The implementation of this functionality can be verified with the tests `test_edit_10pt` and `test_edit_mvc_10pt`.

- **(5 points)** It is required to implement closing a ski slope, if the slope is open. When clicking the **Close**
  button
  from the `list.html` template, the corresponding field in the model should be updated. After that, the page
  `/ski-slopes`
  should be displayed.
    - The implementation of this functionality can be verified with the tests `test_close_slope_3pt` and
      `test_close_slope_mvc_2pt`.

- **(20 points)** It is required to configure login at `/login` and logout at `/logout`. The routes `/` and
  `/ski-slopes`
  are public, while all other pages should be visible only to a user with the admin role. Additionally, in `list.html`,
  the buttons **Edit**, **Delete**, **Add new ski slope**, and **Close** should be visible only to a user with the admin
  role.
  The **Close** button should be visible only if the slope is open.
    - The implementation of this functionality can be verified with the tests `test_security_urls_10pt` and
      `test_security_buttons_10pt`.

- **(10 points)** It is required to enable searching of ski slopes by name (whether the submitted text is contained in
  the `name` field),
  slope length (ski slopes longer than the entered length), slope difficulty, and ski center via the form with
  `id="filter-form"`
  in the `list.html` template. The search results should be displayed on the same page, showing only ski slopes whose
  names
  contain the submitted text, have a greater length than the entered value, match the selected difficulty, and belong to
  the
  selected ski center. Filtering is performed only based on the fields that are filled in (if a field is empty,
  filtering by that criterion is ignored).
    - The implementation of this functionality can be verified with the tests `test_filter_5pt` and
      `test_filter_service_5pt`.

**IMPORTANT**: All mentioned tests are located in the `SeleniumScenarioTest` class.

## Submitting the solution

You must mandatory run the tests, because this is how you submit your solution for evaluation. To check whether your
solution
has been successfully submitted, access the route: [185.153.49.149/submit/[index]](http://185.153.49.149/submit/index),
where `[index]` should be replaced with your student index number, which you must previously enter in the `TODO` value
in the text.

The tests will help you verify the correctness of your implementation, and they will also send information to our server
about how much of your application is working. The code will be reviewed only for students for whom at least one check (
`ExamAssert`) passes successfully.

**It is NOT ALLOWED to modify the tests, nor any part of the `test` package, except for entering your student index
number!**

**YOU MUST ENTER YOUR STUDENT INDEX NUMBER in the appropriate place marked with `TODO` in the `SeleniumScenarioTest`
class!!!**

## Technical instructions:

- In the package `mk.ukim.finki.wp.kol2025g2.model`, the classes that represent the model have already been created.
  You need to map them with the appropriate JPA annotations so that the model can be successfully persisted in the
  database.
  The following conditions apply:
    - One ski slope belongs to exactly one ski resort, while one ski resort can have multiple ski slopes.
    - The identifiers for `SkiSlope` and `SkiResort` must be automatically generated.

- In the package `mk.ukim.finki.wp.exam.kol2025g2.service`, the interfaces for the service logic are already defined.
  For each method, there is a description of what needs to be implemented. You must implement these interfaces in the
  corresponding classes in the package `mk.ukim.finki.wp.exam.kol2025g2.service.impl`. Additional conditions (if any)
  that
  the method must satisfy are explained in the method comments.
- The classes in the package `mk.ukim.finki.wp.exam.kol2025g2.repository` need to be extended with the required methods
  necessary to enable the functionality of the service layer implementation.
  They should extend the `JpaRepository` class from Spring Data.
- You need to annotate the `DataInitializer` class and its corresponding methods so that
  the `initData` method is executed when the application starts.
- In the class `mk.ukim.finki.wp.exam.kol2025g2.SkiSlopeController`, all the required methods are already defined.
  For each method, there is a description of what needs to be implemented. You must map these handler methods using only
  HTTP GET and POST requests.
- Complete the templates with the appropriate **Thymeleaf** attributes to achieve the required functionalities.
  If certain elements or attributes are missing, you may add them, but you must *NOT* change the `id` and `class`
  attributes
  of the existing elements. Comments describe which elements should be repeated and which controller methods should be
  called.
- You need to configure user login and logout using Spring Security in the `SecurityConfig` class.
  The class itself contains a description of what needs to be implemented.