# Hackney ICT Request For Comments

Hackney ICT staff use this repository as a forum to discuss and make technical decisions. The outcomes of these discussions can be either an action plan, or a new standard that Hackney should follow. This repository is open as a reference for staff, local authorities and other digital teams.

## Process

1. Create a new branch on this repository and copy `rfc-000-template.md` to `rfc-XXX-my-proposal.md` (replacing `XXX` with the next available number) and edit.
2. Include any images etc in a separate directory named `rfc-XXX` matching the RFC number and link to them.
3. Make a Pull Request (PR) for your branch and open as a draft.
4. Rename your file and directory with the number of the PR and push changes.
5. When your RFC is ready to be commented on, mark you PR as "Ready for review" and set a deadline for comments (2 weeks is a common choice) and record that in the PR description.
6. Post a link to your PR in the #ict-engineering-team Slack channel
7. Hackney staff discuss your proposal using both inline comments against your RFC document and the general PR comments section. Non-technical staff will need to create a free Github account in order to comment.
8. As changes are requested and agreed in comments, make the changes in your RFC and push them as new commits.
9. Stay active in the discussion and encourage other relevant people to participate. If you’re unsure who should be involved in a discussion, ask your Lead Developer or the Head of Engineering. If you start an RFC it’s up to you to push it through the process and engage people.
10. Once the deadline is reached you are able to merge if the PR has been approved by the Head of Engineering or a Lead Developer (if they haven't or you're not sure, you can contact them on Slack) - this action is the accepting of an RFC.

## Consensus

We're not looking for unanimous excitement about every decision, so there are levels of agreement. Not all disagreements stop us from reaching consensus, but we also want to know if you completely disagree with the proposal. There a few ways you can respond to an RFC:

1. **Agree with the proposal**. Add your approval to the PR.

2. **Agree with reservations**. You're willing to let the proposal go ahead but have concerns or aren't really happy with it. Add a comment (i.e. neither approve the PR nor request changes).

3. **Block/veto the proposal**. Request changes on the PR. This stops the proposal from going ahead in its current form (unless consensus has proven impossible to reach). It's not "I don't like it" but is where you have a fundamental objection.

The author and interested parties are expected to engage with comments and objections to further the RFC. Where an issue is contentious a call or in-person session may be beneficial.

### If consensus isn't reached

Should consensus not be reached by the deadline, one of three things happens. Either:

1. the deadline can be extended; or
2. the RFC can be closed; or
3. the RFC can be accepted/merged IF technical leadership (including the Head of Engineering) agree, and there's little chance of agreeing consensus.

For a deadline extension, you should inform #ict-engineering-team about this status and request extra input. If the RFC is being closed, leave a comment explaining the status and close the PR.

## If the proposal is no longer needed

If the proposal is no longer applicable the RFC PR can be closed. Please include a comment explaining why to help anyone considering the problem in future.

## Editing past RFCs

RFCs should not be substantially altered after they are accepted as they intended to be kept as a point-in-time record of a decision. There are however a few reasons why you may change one that has been accepted:

- to fix typos and other minor mistakes
- to record a status change of the RFC in the YAML frontmatter (remember to update the status_last_reviewed date)
- to mark an RFC as being superseded with a link to the RFC that supersedes it
- any relevant post implementation, or post abandonment, supplementary details that would be useful for someone interested in the area.

## Attribution

This RFC process and template is forked from the [GOV.UK RFCs](https://github.com/alphagov/govuk-rfcs).
