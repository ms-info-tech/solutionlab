# SolutionLab project plan

Updated November 22, 2026.

Describe a need → Get a recommendation → Read the result. Then save a plan and open it later. Use made-up examples, not private information.

The online site is still the first preview. The form, server, and save/open features are built in the local working copy. Editing, deleting, and hosting the full app are next. User access checks are also needed before saved plans can be offered online.

## 1. Enter a need and see a result

**User story:** As a user, I want to describe a technology need so I can get a useful starting point.

**Acceptance criteria**

- A labeled need box and Review options button exist.
- A blank entry or one over 400 characters shows a clear message.
- A valid entry shows a recommendation and a reason.
- The user can choose to save the result.

**Pseudocode**

```text
User enters a made-up technology need.
User selects Review options.
If the entry is blank or too long, show a message and stop.
Otherwise, send the need to the server.
Show the recommendation and its reason.
If the request fails, ask the user to try again.
```

**Status:** Built locally. Not yet added to the online site.

## 2. Get a recommendation from the server

**User story:** As a user, I want the server to handle recommendations so the same rules are used each time.

**Acceptance criteria**

- The page sends the need to an Express API.
- The server checks the entry before using it.
- Simple rules choose an inventory list, task board, calendar, or needs list.
- The API returns the recommendation and reason as JSON.

**Pseudocode**

```text
Receive the request.
Read the need and remove extra spaces at its ends.
If the need is not valid, return an error.
Use the rules to choose a recommendation.
Return the recommendation and reason as JSON.
Show the result on the page.
```

**Status:** Built locally. Recommendations use simple rules.

## 3. Save and open a plan

**User story:** As a user, I want to save a plan so I can read it later.

**Acceptance criteria**

- Save plan stores the need, recommendation, and date in MongoDB.
- The page shows saved plans and lets the user open one.
- Saved plans remain after the local server restarts.
- A failed save shows an error, not a success message.

**Pseudocode**

```text
User selects Save plan.
Check the need and generate its recommendation on the server.
Save the plan in MongoDB.
Show success only after the save works.
Load the list of saved plans.
When the user opens a plan, show its need and recommendation.
If saving or opening fails, show an error.
```

**Status:** Saving and opening are built locally. Editing and deleting are still planned.

## 4. Edit and delete a plan — planned

**User story:** As a user, I want to change or remove my own plans so my saved list stays useful.

**Acceptance criteria**

- Users can change or remove only their own plans.
- An edit is checked before it is saved.
- The user must confirm before a plan is deleted.
- Cancel leaves the plan unchanged.

**Pseudocode**

```text
Select a plan and check that the user may change it.
For Edit, show the current need.
Check the new entry and generate a new recommendation.
Save the changes and show the updated plan.
For Delete, ask the user to confirm.
If confirmed, remove the plan and refresh the list.
If cancelled, leave the plan unchanged.
```

## Project links

- Repository: https://github.com/ms-info-tech/solutionlab
- Public preview: https://ms-info-tech.github.io/solutionlab/
- Existing form story: https://hawk-team-byqo1uak.atlassian.net/browse/SCRUM-5
- Server recommendation story: https://hawk-team-byqo1uak.atlassian.net/browse/SCRUM-6
- MongoDB save/reopen story: https://hawk-team-byqo1uak.atlassian.net/browse/SCRUM-7

Jira may ask you to sign in.

