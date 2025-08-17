# Create feature plan

## Goal

Create a plan for the simplest implementation of `spec/system/$ARGUMENTS.feature`.

## Process

- Read the feature file `spec/system/$ARGUMENTS.feature`
- Read the [glossary](/docs/glossary.md) and [feature guide](/docs/features.md)
- Following an "Outside In" methodology, design a plan for the successful implementation of the $ARGUMENTS.feature
- Write the plan to `docs/tasks/$ARGUMENTS/plan.md`
- Do not start on the implementation itself, only write the plan

## Outside In methodology

We start with a story, describing a feature from the point of view of the principals interacting with the system (from the "outside").  To implement the feature, we move inwards through the layers of the application, from the user-interface or API, through the controllers, the models and eventually the database (the "core"), then moving out again until the response that the principal receives matches the expectations specified in the feature.  

This means that all design work is done from the perspective of the principal, rather than by looking at technical or database considerations.  Which, in turn, results in simpler code and a system that adheres to the YAGNI principle (you are not going to need it).  

### Test Driven Development

At each stage, as new controllers or models are required, we perform "test-driven development", writing specifications for the controllers or models in advance of actually implementing them.  For the purposes of the plan, we just need to note which specs are required with outline of the tests within it.  

- Controller specs must have clauses testing the security of the endpoint, testing for authentication (logged in or not) and authorisation (which roles have access to this endpoint).
- Model specs must have clauses testing invariants, complex associations and important methods

## Process

### Given steps

Given steps denote setup and configuration.  

In most cases this means inserting the correct records into the test database by creating models.  Use information from the glossary to choose which models are required.  The `Fabrik` gem is a factory for models, it is configured in `db/fabrik.rb` and will create models, with their dependencies, so minimal information needs to be specified.  

If it is not possible to configure the database as required, because the models do not yet exist, or additional fields or associations are needed, highlight this in the plan.  

### When steps

These are actions taken by the principal.  

Normally the story starts with a user logging in to the system, then navigating to the relevant page so they can complete the actions required for successful completion of the feature.  

Examine the [routes](/config/routes.rb) to understand which path the principal will follow to perform this navigation.  Then examine the pages they will visit (by looking at the relevant controllers and page components that will be rendered).  If navigation items are missing or require adjustment, highlight this in the plan.  

In order to perform the actions, new routes, controllers, pages, components or forms may be required.  Highlight each of these in the plan.  
### Then steps

These measure the outcomes of the user's actions and verify the feature has met expectations.  

These fall in to two categories - examining the output on the page (what the user sees) and examining the results in the database.  Both are required, but the user output is more important.

### User interface considerations

Features are implemented using Capybara, which drives a remote browser (which is usually headless).  This means that any HTML must be easily parsed and examined so that the output can be tested.  This also has the advantage of encouraging semantic HTML with meaningful element IDs, so the plan should include recommendations for how the output is structured.  

### Existing code

Be aware that most features will be adding to existing functionality within the system.  There will be existing routes, controllers, user-interfaces and models, so be sure to examine any potential effects this feature will have on them and highlight those.  

## output

The plan should be written to `docs/tasks/$ARGUMENTS/plan.md` and the contents should list the required changes to make this feature pass.  

The plan should be aimed at a junior developer and include:

- changes to the routes 
- changes to controllers
- outline specs for controllers (in particular authentication, authorisation)
- changes to the user interface - pages, components and forms
- changes to models (including migrations)
- outline specs for models
