---
description: Do we what?
---

# 💡 What we do

{% hint style="info" %}
T**ips: you can contribute to this document by editing.**
{% endhint %}

### **Deployment Pipeline Checklist**

1. **Ticket Creation (product team)**

* [ ] Product team creates a new ticket in Jira with a clear description and acceptance criteria.
* [ ] Assign the ticket to a developer or development team.

2. **Branching and Development (dev team)**

* [ ] Developer checks out a new branch from the main repository using the ticket ID (e.g., `feature/JIRA-123`).
* [ ] Developer codes the new feature or bug fix or optimize code.
* [ ] Developer writes unit tests or manually tests them by your hand.
* [ ] Commit changes with meaningful commit messages.
* [ ] Rebase from develop branch and fix conflict (if any).

{% hint style="warning" %}
Caution: squash all commits if there are multiple commits ([https://www.geeksforgeeks.org/git-squash/](https://www.geeksforgeeks.org/git-squash/))
{% endhint %}

3. **Code Review (dev team)**

* [ ] Create a Pull Request (PR) in GitHub, referencing the Jira ticket.
* [ ] Include a detailed release note in the PR.
* [ ] Notify the team for code review (can use slack).
* [ ] Address any feedback and make necessary changes.
* [ ] Obtain approval and merge the PR into the develop branch.

4. **Integration and Testing (dev team)**

* [ ] CI/CD pipeline
  * [ ] Triggers automated tests (unit, integration, etc.).
  * [ ] Triggers automated deploy functions change.
  * [ ] Run migrations manually (if any)
  * [ ] Update variable environments (if any)
  * [ ] Update configs (if any)
* [ ] Deploy to a staging environment for further testing.

5. **Notification and Jira Update (product x dev team)**

* [ ] After merging the PR, automatically update the Jira ticket status to "In Review" or "In Testing".
* [ ] Send a notification to Slack with the release note and ticket status update (include referencing the jira ticket).

6. **Production Deployment (product x dev team)**

* [ ] Perform final tests in the staging environment.
* [ ] Bump the version number if applicable (using Semantic Versioning: `MAJOR.MINOR.PATCH`).
* [ ] Deploy the new version to the production environment.
* [ ] Verify the deployment and perform smoke tests.

7. **Post-Deployment (dev team)**

* [ ] Update the Jira ticket status to "Done" or "Closed".
* [ ] Send a final notification to Slack confirming the deployment went live.
* [ ] Document any relevant details or issues encountered during deployment. (change logs)

{% embed url="https://www.mermaidchart.com/raw/2ae2e5bc-bd2e-426c-930e-8c688dd02701?format=svg&theme=light&version=v0.1" %}
Diagram for this pipeline
{% endembed %}

{% hint style="info" %}
Do all this by hand? 🥱 👎 to be continue....
{% endhint %}
