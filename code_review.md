# Code Review 

## Goal

Guidelines for reviewing, assessing and improving the code submitted by another developer.  To be used by the reviewer in conjunction with a project manager or senior developer.  

## Process

Run through each step in turn, making notes as needed.  

- Read the original specification for the work - this may be stored in Linear as "Issue $ARGUMENTS" or in the `docs/tasks` folder as `$ARGUMENTS.md` (ask for clarification if needed).  The task details may be nested as part of a hierarchy of issues, so read the parent issues as well.  
- Fetch the latest version of the `develop` branch, then fetch and switch to the latest version of the feature branch.  
- Merge the `develop` branch into the feature branch, then lint and ensure that tests all pass.  
- Get a list of files that have changed, compared to the `develop` branch.  
- *Briefly* evaluate if the code changes deliver all the required functionality and that the test coverage is adequate.  
- Check all exposed endpoints to ensure they have automated authentication/authorisation tests.  
- Evaluate the changed files against the project style-guide, glossary and documentation.
- Update the project documentation.
- Make your final evaluation
  - ready to be merged 
  - ready to be merged following a user-interface review 
  - should be returned to the original developer with feedback

If you find any minor issues (such as formatting, code style or missing authorisation/authentication tests), resolve them immediately, ensuring any fixes follow the project style guide.  For other issues, remedies are detailed within each step, below.  

### Read the Specification

Read and understand the original specification for the work so that the code can be evaluated for functional completeness.  Make temporary notes if required.  

### Merging

The "trunk" code for the project is in the `develop` branch (or `main` for smaller projects).  The work to be reviewed will be in a specific feature branch.  

To ensure that the feature branch is up to date with trunk:
- Fetch the latest trunk branch
- Merge it into the feature branch
	- Fix simple merge conflicts immediately
	- Ask the manager to resolve complex merge conflicts
- Lint the merged code
- Run the tests
  - If there are any failures, present a report and ask the manager how to proceed

### Evaluations 

List the files that have changed between the feature branch and the project trunk.  

#### Functionality

Think hard and evaluate if the code changes cover the requirements detailed in the specification?  Do those changes have adequate test coverage?

Present a report to the manager before proceeding.  

#### Security, Authentication and Authorisation 

Run `bin/brakeman` to perform a static security analysis on the codebase.  

Does this feature require new permissions to control read and write access to entities within the system?  

If so, and the project uses the CanCanCan gem for authorisation:
- Has the `app/models/ability.rb` file been updated accordingly?  Have the specs for the ability file also been updated to ensure access is controlled as expected?

Is any new functionality exposed to the web?  
- Controllers added or updated?
- Routes renamed or added?
- LLM tools added or changed?

If so:
- Are there automated tests for each of those files?  
- Do those automated tests verify:
  - authentication - what happens when not logged in?
  - authorisation - what happens when logged in without the correct permissions?

If any issues are found, plan a resolution, then present this plan to the manager and ask how to proceed.  

#### Style 

Compare the changed files to the style guide.  If the code deviates from the style guide, present a report to the manager and ask how to proceed.  

If there is a project glossary, do any new terms introduced by these changes fit into the previous vocabulary?  Has the glossary been updated to match the new functionality?  If terms require adding or updating, present a report to the manager and ask if it is OK to make those changes.  

### Documentation 

#### User Documentation 

Do the project documentation and project README match the new feature?  

For each user role involved in this specification, is there documentation, in `docs/features/$user_role` explaining how to make use of the feature?  

If changes are required, present a report to the manager and ask if it is OK to update the documentation.  

Remember the documentation should reflect how it _actually_ works, not what was originally specified - and the ultimate aim is that the `docs/features` repository becomes a useful knowledge base on how to make best use of the system.  

#### API documentation

Have there been any changes to the JSON API?  

If so, regenerate the OpenAPI specification by running `OPEN_API=1 bin/rails spec:requests`.  This will regenerate the OpenAPI specification in `public/api-docs` - and commit the changes.  

#### Database Seeds

Have the database seeds `db/seeds.rb` and factory configuration `db/fabrik.rb` been updated?

If there have been models added or the feature requires a different configuration or setup, then the factories should be updated to reflect the new requirements and the seeds updated so that useful data is available every time a fresh installation of the software is done.  

If either of these are required, think hard about the new seeds that will be required, present a report to the manager, then ask how to proceed.  

## Final Output 

After the various evaluations, the final output should be an evaluation of the work done: 

- this work is ready to be merged
- this work includes user-interface changes so requires a visual inspection before merging
- this work has one or more issues and should be returned to the original developer with feedback

If the Github PR can be derived from the Issue ID $ARGUMENTS, then add the evaluation as a comment on the Github Pull Request, as well as presenting the output to the manager.

## Final Instructions 

1. No code should ever be merged without adequate automated security tests
2. Always follow the project style guide for amendments to the code
3. Returning a review to the original developer helps with learning and improving the team.  Ensure feedback is constructive and explains why the code is being returned without harsh judgement.  