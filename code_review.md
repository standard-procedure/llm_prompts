# Code Review 

## Goal

To guide an AI assistant in reviewing, assessing and improving the code submitted by another developer.  The original work request will be available as an issue in Linear (with ID $ARGUMENTS), the code for review will be in a feature branch and the main body of code will be in the `develop` branch.  

## Process

1. Read Issue ID $ARGUMENTS from Linear.  The Issue may be nested as part of a hierarchy of nested sub-issues, so if clarification is required, read the parent issues as well.  
2. Fetch the latest version of the `develop` branch, then fetch and switch to the latest version of the feature branch.  
3. Merge the `develop` branch into the feature branch, then lint and ensure that tests all pass.  
4. Get a list of files that have changed, compared to the `develop` branch.  
5. *Briefly* evaluate if there is any required functionality that has not been delivered - and for the work that has been delivered, is it covered by adequate tests.  
6. Check to see that all endpoints have specs for authentication and authorisation - security is vitally important so we need automated tests to prove our system meets the basic requirements.  
7. Evaluate the changed files with the project style-guide and glossary.
8. Are these changes ready to be merged into the `develop` branch? 
   - ready to be merged, or 
   - ready to be merged following minor amendments, or 
   - should be returned to the original developer with feedback

It is important to remember that it is OK to stop and ask for help.  The point of the review is to make things better for everyone working on the project, so consensus is good.  

Also, there may be some changes which are better returned to the original developer to complete.  It helps them meet the high standards that we expect and teaches best practices.  Always bear in mind that we are often dealing with junior developers who may not have a full understanding of the implications of their coding choices, so, if feedback is required, it's always important to be kind and helpful, rather than harsh and judgemental.   

### Merging

The AI should merge the `develop` branch into the feature branch to ensure that the latest trunk work is included.  

If there are merge conflicts, try to understand if it is a simple fix.  If it is _very_ simple then fix the conflict and complete the merge.  But if there is any doubt, pause and ask for help.  

### Linting

Once the merge has been completed, the project should be linted using `standardrb --fix` and any updates committed to the feature branch.  However, if there are any issues that cannot be automatically fixed, either fix them immediately or ask for help.  

### Specs 

Make sure that the specs all pass, using `bundle exec rspec`.  

If there are any failures, check if it looks like an easy fix.  If so, correct the code, commit and run the specs again.  However, if it looks like a complex fix, or it is not resolved in three or four iterations, stop and ask for help.  

### Evaluations 

#### Functionality

Do the code changes cover the requirements detailed in Issue $ARGUMENTS?  And are those requirements covered adequately by tests to prove that they work as expected?

#### Security 

As security and privacy are of vital importance, are all web-accessible end-points protected by the relevant authentication and authorisation mechanisms?  

Are there automated tests to prove this is the case, now and into the future?  In some cases this may be as simple as "HTTP status 401 if not logged in, HTTP status 200 if logged in".  In other cases, it may result in different outcomes based upon the permissions assigned to the user.  

You can also use `bin/brakeman` as a static security analysis tool - to highlight potential issues with the code.  

As ever, stop and ask for help if needed - security is a big and important topic.  

#### Style 

Compare the changed files to the style guide and if there are simple changes to make, do them and commit them.  

If there is a project glossary, do any new terms introduced by these changes fit into the previous vocabulary?  Has the glossary been updated to match the new functionality?  If not, make the changes if they are small, or stop and ask, if they are larger.  

## Output 

After the various evaluations, the AI should give us an answer that says that changes in this feature branch: 

* meet the functional and general requirements from the issue and can be merged to `develop`, or 
* were not quite up to standard, but some simple fixes were committed and now the branch can be merged, or 
* cannot be merged as some revisions, as mentioned in the attached notes and observations, are needed.  

If the Github PR can be derived from the Issue ID $ARGUMENTS, then the Github Pull Request should be updated directly - with the changes pushed and either the PR merged and closed or the comments posted for review by the original developer.  

## Final Instructions 

1. Treat security very seriously 
2. Project style is subjective but keeping everyone on the same page aids productivity so is also important
3. Feedback should be understanding and provided with the aim of helping everyone improve.  