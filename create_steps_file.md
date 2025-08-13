# Create steps file

## Goal

Create a [steps file](https://github.com/jnicklas/turnip) for a feature.  

## Process

- Read the feature file `spec/system/$ARGUMENTS.feature`
- Identify each step within the feature file
- Create a steps file in `spec/system/steps/$ARGUMENTS_steps.rb` 
- Add a module definition for the file, then implement skeleton step definitions for each step in the feature file

## Translating from a feature file to the ruby steps file

The `spec/system/$ARGUMENTS.feature` will be in [Gherkin format](https://cucumber.io/docs/gherkin/reference/): 

- Title
- User story
- Scenario
  - Given 
  - When 
  - Then 
- Scenario
  - Given 
  - When 
  - Then 
  
Each "Given", "When" or "Then" clause is a "step" (for readability purposes they can also start with "And" or "But").  Each step then has an equivalent `step` definition in the ruby `spec/systems/steps/$ARGUMENTS_steps.rb` file.  

For example: 

- `Given an active account`
```ruby
step "an active account" do 

end
```

- `When I log in`
```ruby
step "I log in" do 

end
```

- `Then I see the results of the calculation`
```ruby
step "I see the results of the calculation" do 

end
```

A step may contain placeholder values.  These are in quotation marks and are replaced by a variable in ruby code.  

- `And an employee called "Alice Aardvark"`
```ruby
step "an employee called :name" do |name|

end
```

The ruby steps file must have a containing module; this should have a name relating to the feature it is implementing.  

For example "spec/system/inviting_users.feature" would be written to "spec/system/steps/inviting_users_steps.rb" and contain `module InvitingUsersSteps`.  

