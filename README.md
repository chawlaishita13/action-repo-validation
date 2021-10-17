# GitHub Action for Validating Action Repositories
This is a GitHub Action to validate action repositories. There are certain validations that need to be checked in an Action repository. For instance, it is ideal for an Action repository to have a README file with an Example workflow and Contribution Guidelines.

With this Action, you can check for essential validations for an action repository listed below. For every check, either a success message will be displayed or an error will be thrown.   

## Validations for an Action repository



1. The action should have a readMe having information about the action. It should include : \
a. At least one Example workflow \
b. Contribution guidelines
2. The code owners should be mentioned in a CODEOWNERS file in .github folder. Here is one [sample file](https://github.com/Azure/actions/blob/main/.github/workflows/CODEOWNERS).
3. For typescript actions, node_modules should: \
a. Not be present in master/main branch \
b. Be present in releases/* branch
4. Proper branch permissions should be set, PRs in main and releases/* branch should require at least one approval. More information on branch protection can be found [here](https://docs.github.com/en/github/administering-a-repository/defining-the-mergeability-of-pull-requests/managing-a-branch-protection-rule).
5. Security and vulnerability BOTs should be set up for the repo. Dependabot alerts and Dependaobot security updates should be set up in the repository Settings. 
![image](https://user-images.githubusercontent.com/58769601/123243496-b5199100-d500-11eb-9524-6589e4671ca7.png)

6. An issue template should be defined to set the default label as need-to-triage.One can follow these [steps](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository)  to set up a template. 

7. The repo should have some standard labels defined. The following labels should be there : 
<table>
  <tr>
   <td><strong>Label</strong>
   </td>
   <td><strong>Description</strong>
   </td>
   <td><strong>Color (Optional)</strong>
   </td>
  </tr>
  <tr>
   <td>need-to-triage	
   </td>
   <td>Requires investigation
   </td>
   <td>#fbca04
   </td>
  </tr>
  <tr>
   <td>idle 
   </td>
   <td>Inactive for 14 days
   </td>
   <td>#9A777A
   </td>
  </tr>
  <tr>
   <td>question	 
   </td>
   <td>Requiring some clarification
   </td>
   <td>#d876e3
   </td>
  </tr>
  <tr>
   <td>bug
   </td>
   <td>Something is not working
   </td>
   <td>#d73a4a
   </td>
  </tr>
  <tr>
   <td>P0
   </td>
   <td>Action not working
   </td>
   <td>#B60205
   </td>
  </tr>
  <tr>
   <td>P1
   </td>
   <td>Some scenario broken but workaround exists
   </td>
   <td>#EE3D1D
   </td>
  </tr>
  <tr>
   <td>enhancement	
   </td>
   <td>Feature request/improved experience
   </td>
   <td>#a2eeef
   </td>
  </tr>
  <tr>
   <td>documentation	
   </td>
   <td>Improvements or additions to documentation
   </td>
   <td>#0075ca
   </td>
  </tr>
  <tr>
   <td>backlog
   </td>
   <td>Planned for future
   </td>
   <td>#bd7e4b
   </td>
  </tr>
  <tr>
   <td>performance-issue	
   </td>
   <td>Performance improvement required
   </td>
   <td>#0e8a16
   </td>
  </tr>
  <tr>
   <td>waiting-for-customer
   </td>
   <td>Waiting for inputs from customer
   </td>
   <td>#0e8a16
   </td>
  </tr>
</table>

## Input
`GITHUB_TOKEN`: Personal access token of your repository. Uses your access token PAT_TOKEN.

## Output
All required validations will be run and a success mesage or an error will be shown in the console as output.

## Example
```yml
name: "build"

on:
  pull_request:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v1
    - name: Testing action
      uses: ishitachawla/action-repo-validation@releases/1
      with:
        GITHUB_TOKEN: ${{ secrets.PAT_Token }}
```

# Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
