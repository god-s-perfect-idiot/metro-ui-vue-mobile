# Pull Requests and Issues

## Pull Requests

You can contribute to the project by creating a pull request. To create a pull request, you need to fork the repository and then clone it to your local machine. Then you can make changes to the code and push it to your forked repository. Then you can create a pull request from your forked repository to the main repository. Please make sure that you have read the contributing guidelines before creating a pull request. Please do not create a new branch on the repository for your pull request. You can create a pull request from the main branch.

When Creating pull requests, use the following template:

    ```markdown
    ## Description
    <!--- Describe your changes in detail -->
    
    ## Motivation and Context
    <!--- Why is this change required? What problem does it solve? -->
    <!--- If it fixes an open issue, please link to the issue here. -->
    
    ## How Has This Been Tested?
    <!--- Please describe in detail how you tested your changes. -->
    <!--- Include details of your testing environment, and the tests you ran to -->
    <!--- see how your change affects other areas of the code, etc. -->
    
    ## Screenshots (if appropriate):
    
    ## Types of changes
    <!--- What types of changes does your code introduce? Put an `x` in all the boxes that apply: -->
    - [ ] Bug fix (non-breaking change which fixes an issue)
    - [ ] New feature (non-breaking change which adds functionality)
    - [ ] Breaking change (fix or feature that would cause existing functionality to not work as expected)
    - [ ] Documentation update
    - [ ] Other (please describe):
    
    ## Checklist:
    <!--- Go over all the following points, and put an `x` in all the boxes that apply. -->
    <!--- If you're unsure about any of these, don't hesitate to ask. We're here to help! -->
    - [ ] My code follows the code style of this project.
    - [ ] My change requires a change to the documentation.
    - [ ] I have updated the documentation accordingly.
    - [ ] I have read the **CONTRIBUTING** document.
    - [ ] I have added tests to cover my changes.
    - [ ] All new and existing tests passed.
    ```

## Issues

You can create an issue in the issues tab. To create a new issue, you need to click on the new issue button and then fill in the details. When creating issues, it is good if you could provide the appropriate labels and milestones and making sure to provide sufficient context. Use the following template when creating issues:
    
    ```markdown
    ## Description
    <!--- Provide a more detailed introduction to the issue itself, and why you consider it to be a bug -->
    
    ## Expected Behavior
    <!--- Tell us what should happen -->
    
    ## Current Behavior
    <!--- Tell us what happens instead of the expected behavior -->
    
    ## Possible Solution
    <!--- Not obligatory, but suggest a fix/reason for the bug, -->
    
    ## Steps to Reproduce
    <!--- Provide a link to a live example, or an unambiguous set of steps to -->
    <!--- reproduce this bug. Include code to reproduce, if relevant -->
    1.
    2.
    3.
    4.
    
    ## Context (Environment)
    <!--- How has this bug affected you? What were you trying to accomplish? -->
    <!--- Providing context helps us come up with a solution that is most useful in the real world -->
    
    ## Detailed Description
    <!--- Provide a detailed description of the change or addition you are proposing -->
    ```

## Contributing Guidelines

To contribute to the project, you need to follow the following guidelines:
- Please do not modify the README.md file unless you are contributing to the README.md file alone in the PR.
- Please do not modify the LICENSE file under any circumstances.
- Please do not modify the .gitignore file under any circumstances.
- Please do not modify the .prettierrc file under any circumstances.
- Please do not modify the .eslintrc.js file under any circumstances.
- Please do not modify the ts config files or vite configs under any circumstances.
- When creating new Components, make sure the name of the component is in PascalCase. For example, `MyComponent.vue`.
- Each component should have its own test file. For example, `MyComponent.spec.ts`.
- When creating variables, make sure the name of the variable is in camelCase. For example, `myVariable`.
- When creating functions, make sure the name of the function is in camelCase. For example, `myFunction()`.
- When creating interfaces, make sure the name of the interface is in PascalCase. For example, `MyInterface`.
- When creating types, make sure the name of the type is in PascalCase. For example, `MyType`.
- When creating enums, make sure the name of the enum is in PascalCase. For example, `MyEnum`.
- When creating constants, make sure the name of the constant is in PascalCase. For example, `MY_CONSTANT`.
- When creating classes, make sure the name of the class is in PascalCase. For example, `MyClass`.
- When creating mixins, make sure the name of the mixin is in PascalCase. For example, `MyMixin`.

## Project Structure
src/components: Contains all the components used in the project. 
src/assets: Contains all the assets used in the project.
src/router: Contains the router file.
src/store: Contains the store file.
src/types: Contains all the types used in the project. (TBW)
src/utils: Contains all the utility functions used in the project. (TBW)
src/views: Contains all the views used in the project.
src/App.vue: The main app file.
src/main.ts: The main file.
src/components/__tests__: Contains all the tests for the components used in the project.
src/components/fragments: Contains all the fragments used in the project. These are the components that are used in multiple components.
