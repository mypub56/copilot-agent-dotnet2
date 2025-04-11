# GitHub Copilot Workshop

This workshop demonstrates how to interact with GitHub Copilot in different modes to develop a .NET 9 Blazor application.

## Part 1: Using GitHub Copilot Chat in Edit Mode

GitHub Copilot Chat in Edit Mode helps you modify existing code or get guidance on what to write next. Here are some example prompts:

### Step 1: Install SQLLite
> **Prompt**: Could you install SQLListe for me please? The instructions are available here: #file:Setup-SqlLite.md

### Step 2: Create an empty database
> **Prompt**: Could you setup my DB for me it should be nammed MuseumOfBadIdeas foolow the instructions from the guide.

### Step 3: Technical Requirements
> **Prompt**: Create the technical instructions in docs/Technical-Instructions.md to setup the requirements for my components.
I want to use .NET 9 and Blazor. Of course I will use my SqlLite database: MuseumOfBadIdeas and use entity framework to access to this database.
Please ensure that the fiels will not contains multiple classes in it keep it in different files. 
I would also like to use the nugets:
> - AutoMapper
> 
> For the unit test I want:
> - Fluent Assertions
> - xUnit

### Step 4 : Steps
Could you create a list of all the technical steps and details to accomplish my project. Please refer to #Project.md and #Technical-Instructions.md


## Part 2: Using GitHub Copilot Chat in Agent Mode

GitHub Copilot Chat in Agent Mode can perform actions on your behalf, such as creating projects and modifying multiple files.

### Step 5: Complete Project Creation
> **Prompt**: Could you create the project for me please? The description of the project is in #file:Project.md. You can find the requirements in #file:Setup-Requirements.md and #file:Setup-SQL.md. The necessary steps are described in #file:Steps.md.