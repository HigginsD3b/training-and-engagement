# CFDE Training Website Release Plan

This is the release plan for the [CFDE training website](https://cfde-training-and-engagement.readthedocs-hosted.com/en/latest/).
This plan has sections to address the different release management topics:

-  Definition of release numbering and naming convention
-  Definition of expected release frequency
-  Locations for release documentation, repo etc
-  Roles and responsibilities for the releases
-  Definition of steps in a release cycle

## Release Dates

Timeline for release 2020-2021


| Release # | Date | Month     | Year | Version tag |
| --------- | ---- | --------- | ---- | ----------- |
| 1         | 15   | August    | 2020 | 2020.08     |
| 2         | 15   | October   | 2020 | 2020.10     |
| 3         | 15   | December  | 2020 | 2020.12     |
| 4         | 15   | March     | 2021 | 2021.03     |
| 5         | 15   | June      | 2021 | 2021.06     |
| 6         | 15   | September | 2021 | 2021.09     |
| 7         | 15   | December  | 2021 | 2021.12     |


Our current release dates are set to coincide with NIH deliverable dates.


#### Labels Format
Name: release.month(short form)-release.year
For example, *Oct-2020*.

## Release Checklist

A series of checklists will be implemented to ensure error free working tutorials are released to the public.

### Tutorial Format

Individual tutorials will follow the formatting, organization, and layout details described in the [training website style guide](../CFDE-Internal-Training/Website-Style-Guide/0index.md).

### Tutorial PR Process

Individual branches are used to create PRs to merge into `dev`. Good practices for creating PR branches are:
- create a new branch off `dev`
- name the branch with included feature/fix/content along with PR author's name. e.g. scanchi-mime-new or marisa-sphinx-javascript or abhijna_kf_edits
- keep the PR branch up to date with `dev` by pulling latest merged changes. *Note on the GitHub interface for the PR you will get an indication to update your branch which essentially merges latest changes in `dev` to your branch*
- After the PR has been successfully merged, delete the branch in your remote and local repos

Generally we want to avoid merging between branches with open PRs. This is because by committing the changes between branches, they effectively become the same branch. Thus, when one branch is merged, the other branch with the same commit log will be automatically merged irrespective of the review stage. However, in a scenario where there might be dependency between branches, one can merge one branch into the other restricting it to only one direction. For example, we have PR A and PR B on two different branches and the fixes in PR A are relevant to PR B. We would then merge the branch for PR A into the branch for PR B but not vice versa. Alternatively, if the PR is not time sensitive, then one can wait for PR A to merge into `dev` before pulling those changes into PR B.

### Tutorial PR Checklist

The PR author should ensure:
- a descriptive title - title should describe PR changes that will be added to release notes
- clean build logs - automated check for correct documentation build
- colorblindness test https://www.toptal.com/designers/colorfilter/
- correct rendering of website (preview of their branch using autogenerated RTD link)
- resolution of any merge conflicts
- release label - tagging the upcoming release, e.g. `Oct-2020`
- PR type label - `new` for new content, `feature` for new features, `fixes` for updates and fixes to existing content
- assignment to the appropriate project - project board for a given release for tracking
- linking of related issues - if applicable

Note that for a PR to be included in the release notes, it needs to be associated with **both** the release label and the PR type label. It is also possible to add labels and edit titles after the merge but prior to the internal release deadline.
For clarity, the PR title should include the tutorial name and main intent of the PR. 
- Example PR title for a new tutorial: Enabling/Javascript adding content chooser and integration of content tabs and superfences
- Example PR title for fixes to existing tutorial: Rendering/Jekyll and Working/Branches learning objectives and pre-reqs added 

### Reviewer Checklist for PR

Following the PR to merge into `dev`, the reviewers must ensure the tutorials pass the checklist for:
- spelling and grammar
- successful run of all installation and code chunks
- sufficient explanation and details for the tutorial content - suggestions for inclusion of admonition boxes or additional resources for clarity
- code syntax and naming convention - ensure code chunks have a logical progression and clear explanations
- adherence of tutorial format to style guide
- functional links (inter and intra) - check the automated broken links check for clean build, suggest intra links if applicable
- accessible hyperlink text - meaningful text hyperlinked instead of default "click here"

The reviewer checklist will be auto-generated as a comment on any open PR to `dev` branch. The list will appear in raw markdown format but will render as a checklist after the list is copied, pasted, and submitted as a comment. This will allow each reviewer to have an independent checklist that can be updated as the review progresses.

### Review Process

The review process is split between the two levels of merge. Individual branches get merged into `dev` and all the changes for a release are collectively merged from `dev` into `stable` which is the base for the public facing website.

Merge into `dev` from individual branches requires two reviews while merge into `stable` requires group approval. Currently, automated reviewer assignment has been implemented which assigns the correct number of reviewers depending on the merging branch. However, if a team member with experience in a tutorial topic is not assigned to review the tutorials, one can manually add an additional reviewer. Alternatively, that team member can offer their review in the form of comments on the PR. Reviewers can also be manually unassigned if necessary. While both the manually added and auto assigned reviewers will be notified via the GitHub notification, the PR author should make sure to communicate with the reviewers for timely review and any necessary clarifications.

## Release Cycle

Each Release cycle will be defined as the time period between the releases. The release cycle will have some set phases:
- Tracking
- Planning
- Development
- Internal release deadline
- Final merge
- Public release

The overall workflow is visualized in the flow diagram of the release process.

![Training release process](../images/Release_workflow_training_repo.png)

### Tracking

Using 'Projects' in GitHub we will create and track issues throughout the release cycle.

### Planning

Each release cycle there are different tasks to be completed:
- new tutorial development
- fixes to existing tutorials
- GitHub management - creating issues and labels - tracking
- new tutorial reviews
- general reviews
- reviews for merge into `stable`
- release notes maintenance

The planning phase scheduled following a release will allow for discussion and assignment of the different roles for the upcoming release. This phase will also include discussion for generating new content and creation of appropriate issues in the training repo.

### Development

This phase will include work on developing new content and enhancing published tutorials.

- Authors developing new tutorials should allow for at least 1 week for the review process in their plans
- When possible include installation and setup steps across all target platforms (Mac, linux, Windows)
    - Provide links to setup instructions if they already exist as standalone tutorials
    - For overlapping setup instructions that are part of an existing tutorial, check if the setup instructions can be reorganized into standalone modules 
- To ensure tracking and linking of related issues, the authors involved in tutorial creation or fixes should create related issues in the training-and-engagement GitHub repo and assign appropriate labels for the release.

### Internal release deadline

Internal Release Deadline: five business/working days prior to release date

Checklist for internal release:
   - all PRs tagged for the upcoming release should be prepared for successful merge into `dev` and been successfully rendered.
   - the original PR author should ensure all review comments (if any) are addressed prior to merge.
   - all new tutorials should follow the style guide for formatting and tutorial arrangement.
   - if changes requested from a reviewer on a PR cannot be completed by the internal release deadline, the PR author should relabel with the next release date.
   - connect intra tutorials that were merged into `dev` if applicable

### Final merge

This phase will involve merging `dev` into `stable`. Allotted timeline would be 5 business/working days until release date.

This phase will involve finalizing release-notes for the website. A draft of the release notes will be auto generated based on PR merges into `dev`.  
To access the draft
- access the `Releases` tab on the main repo page
- click on `Create a new release`
- subsequently click on `Releases`
- use the `Edit` button on the right top corner
- modify the release titles if applicable, add date and save draft

The release information will also be documented in a markdown file `index.md`, hosted within `Release Notes` folder under the `/docs` folder structure of the training repo in Github. Editing of the the website release version will include removing `Website Features` category, intra linking of tutorials mentioned and documenting changes to existing tutorials under the `Updates and Fixes` category. Addition of enhancements features like vidlets, images, screencasts etc to existing tutorials can be highlighted in a separate category (Enhancements or Improvements) if applicable.

The release notes will also be referenced in the landing page of the training website.

Merging from `dev` to `stable` requires group approval. For this phase, one PR will be opened for merge into `stable` and the approval for merge will be based on the rendered website with the following checklist:
   - If new features were merged check for functionality across entire site
   - Check for tutorial rendering on multiple browsers, modes (normal, incognito) and devices (phone, tablet, laptop)
        - Chrome
        - Safari
        - Edge
        - Firefox

### Public release

After the creation of release notes and the successful merge of `dev` into `stable` we will announce the release on GitHub, Twitter, the website, and through the CFDE Newsletter.

Jose and Jeremy handle the newsletter while Titus and Amanda handle the twitter page for CFDE. All of them should be tagged and/or pinged after the release for appropriate announcements.  

## Release Documentation

The Github repo for the training website will host a release section and associated tag information.

For documentation version numbering system we will follow the release date convention. Thus our release tag would have the format: **`YYYY.MM`**

For example October 2020 release would have the tag **`2020.10`**. This would follow the same convention as set for labels on GitHub repo.

For the public release on GitHub repo, set the default branch to `stable` and add release tag.

Release format for the public website:

 > Latest Release
 >
 > Updated Release.Month Release.Date, Release.Year
 >
 > New Tutorials
 > Links to new tutorials added in the current release
 >
 > Improvements or Enhancements (optional)
 >
 > Any enhancements to tutorials or website features. This would include any additional screencasts, vidlets,
 images that were added to tutorials and integrated website features
 >
 > Updates and Fixes
 >
 > This section will highlight any code or link fixes to existing tutorials in addition to any clarification notes and explanation that was added.