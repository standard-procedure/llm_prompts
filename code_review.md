# Code Review 

## Goal

To guide an AI assistant in reviewing, assessing and improving the code submitted by another developer.  The original work request will be available (either as an issue in Linear with ID $ARGUMENTS, or as a text file in `docs/tasks/$ARGUMENTS.md`).  The code for review will be in a feature branch and the main body of code will be in the `develop` branch.  

## Process

- Read issue $ARGUMENTS from Linear or the `docs/tasks` folder.  The Issue may be nested as part of a hierarchy of nested sub-issues, so if clarification is required, read the parent issues as well.  
- Fetch the latest version of the `develop` branch, then fetch and switch to the latest version of the feature branch.  
- Merge the `develop` branch into the feature branch, then lint and ensure that tests all pass.  
- Get a list of files that have changed, compared to the `develop` branch.  
- *Briefly* evaluate if there is any required functionality that has not been delivered - and for the work that has been delivered, is it covered by adequate tests.  
-  Check to see that all endpoints have specs for authentication and authorisation.
- Evaluate the changed files with the project style-guide, glossary and documentation.
- Update the documentation.
- Make your final evaluation
  - ready to be merged 
  - ready to be merged following a user-interface review 
  - should be returned to the original developer with feedback

If an issue is found, describe the problem and ask the user if the AI should fix it or if it should be returned to the original developer.  This teaches the developer best practices and helps them meet the high standards that we expect.  Bear in mind that we are often dealing with junior developers; if feedback is required, be kind and helpful, not harsh and judgemental.   

### Merging

The AI should merge the `develop` branch into the feature branch to ensure that the latest trunk work is included.  

If there are merge conflicts, try to understand if it is a simple fix, present a report and ask the user how to proceed. 

### Linting

Once the merge has been completed, the project should be linted using `standardrb --fix` and any updates committed to the feature branch.  However, if there are any issues that cannot be automatically fixed, present a report and ask the user how to proceed. 

### Specs 

Make sure that the specs all pass, using `bundle exec rspec`.  

If there are any failures, present a report and ask the user how to proceed. 

### Evaluations 

#### Functionality

Do the code changes cover the requirements detailed in $ARGUMENTS?  And are those requirements covered adequately by tests to prove that they work as expected?

#### Security 

Security and privacy are of vital importance; are all web-accessible end-points protected by the relevant authentication and authorisation mechanisms?  

Are there automated tests to prove this is the case and prevent regressions?  In some cases this may be as simple as "HTTP status 401 if not logged in, HTTP status 200 if logged in".  In other cases, it may result in different outcomes based upon the permissions assigned to the user.  

Use `bin/brakeman` as a static security analysis tool - if issues are found, present a report and ask the user how to proceed. 

#### Style 

Compare the changed files to the style guide and if the code requires changes present a report and ask the user how to proceed. 

If there is a project glossary, do any new terms introduced by these changes fit into the previous vocabulary?  Has the glossary been updated to match the new functionality?  Make the changes if necessary.

Are the project README and any relevant documentation in the `docs` folder accurate and up to date?

Does the documentation match the new feature?  The documentation should represent how the system currently works, not how it was specified, so if there have been deviations, ensure the documentation is up to date.  

### Documentation 

This step only applies to Feature Specifications.  

If there is an original Feature Specification (either in `docs/tasks` or in Linear) describing the work done here, evaluate it and see if the work that has been done matches the requirements.  During implementation we have had to adjust the requirements, so there may be differences.  

Then copy the original specification or report to `docs/features`, updating the contents to reflect that actual work done.  The aim is that `docs/features` becomes a live documentation repository detailing how the system works.  

## Output 

After the various evaluations, the final output should be an evaluation of the work done: 

- this work meets the functional and general requirements and is ready to be merged
- this work meets the functional and general requirements but includes user-interface changes so requires a visual inspection before merging
- this work has one or more issues and should be returned to the original developer with feedback

If the Github PR can be derived from the Issue ID $ARGUMENTS, then add the evaluation as a comment on the Github Pull Request, as well as presenting the output to the user.

## Final Instructions 

1. Treat security very seriously 
2. Project style is subjective but keeping everyone on the same page aids productivity so is also important
3. Issues with the code should be returned to the original developer for completion and feedback should be understanding and aim to help everyone improve.  