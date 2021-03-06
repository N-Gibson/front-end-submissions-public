### Evaluator: Robbie
### Students: Eric
### Comments:

* The weight calculator is a nice addition!
* On wider screens, looks like the main page is cutoff at the bottom
* Overall a cool grouping of space things
* 1 failing test at time of eval and some linter warnings
* I would expect these routes ` <Route exact path="/venus" render={ () => <PageContainer ...` to be dynamic - something like `http://localhost:3000/planets/earth` where the planet name is dynamic `http://localhost:3000/planets/:planet`, this will reduce a lot of repetition
* Mercury and Mars are so close in mass!
* Tell more about `resetStoreCalculation(dispatchNumber)` in the `NavLink`s

## Rubric 

### Specification Adherence

* 3 - The application completes all iterations above without error. Evaluator has minimal recommendations for design changes.

### Project Professionalism

* 3 - The codebase has less than 5 linter errors and README has been updated with all group members. Project utilized wireframes from the outset and updated them as changes were made. A project management tool was continuously used from the beginning of the project.  All git commits are atomic, made first to branches, and use descriptive and consise commit messages. 

### React Architecture

* 3 - React architecture is clean and organized.  Logic is kept out of return statements.  There are some issues with the asynchronous js where the frontend is not matching with the backend.  There are multiple functions (including fetch calls) that are doing similar pieces of functionality that could continue to be refactored. Data fetched from API is not cleaned before being set to state.

### Redux Architecture

* 3 - Appropriate components are wrapped in connected Redux container components. The Redux store contains all necessary application data. All state changes are handled through Redux actions and reducers.

### Testing

* 3 - All Redux functionality is tested (actions, reducers, mapStateToProps, mapDispatchToProps), all components are unit tested, and a valid attempt was made to test any async functionality.
* 4 - All async functionality is tested.   Asynchronous tests cover happy paths as well as multiple sad paths.  All pieces of functionality have been tested and are passing and run efficiently (using mount only when appropriate). Evaluator has no recommendations for testing.

### Routing

* 3 - Application uses React Router to display appropriate components based on URL.  UX is clear and set up well so that user has access to previous routes.
