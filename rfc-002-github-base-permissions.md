# Set the GitHub base permission to "none"

## Summary

The current base permission of `write` for our GitHub organisation is too permissive. Reducing the base permission to `none` improves our security posture, and enables better management of senstive or personal projects.

## Problem

At some point in the distant past, possibly when `LBHackney-IT` was first created, the base permission was set as  `write`. The base permission is the default permission set assigned to every user we add to the organisation.

Now we have a few different groups leveraging our GitHub organisation to host repositories and share code. These include (but aren't limited to):

- Engineering
- Cloud Engineering
- Data Platform (and contributors to/users of the Data Platform who are not part of ICT)
- Public Health

As all contributors have write permission, anyone added to the organisation automatically gain more permissions than they need, including being able to push code to any repository (and therefore to trigger builds and access SSH debug sessions in CircleCI).

The base permission also means there is no such thing as a "private" repository – all repositories are automatically visible to everyone. This means we have no way to restrict access to repositories with known irrevokable secrets or sensitive content

## Proposal

1. Reduce the base permission from `write` to  `none`.

## Consequences

1. All projects which aren't owned or maintained by the team a person belongs to will become read-only. There are currently only `public` and `internal` repositories, all of which are visible and read-accessible to anyone in the `LBHackney-IT` organisation.

2. Any repositories which receive regular contributions from multiple teams will need those teams adding with `write` permissions. For example, the [Development Team](https://github.com/orgs/LBHackney-IT/teams/development-team) has `write` access to the [`LBHackney-IT/ce-dns`](https://github.com/LBHackney-IT/ce-dns).

3. Occasional contributions from people outside the owning team would require either:
    - Forking the repository then proposing changes from the fork (described [here](https://docs.github.com/en/get-started/exploring-projects-on-github/contributing-to-a-project)); or
    - Temporarily granting `write` privileges to the outside team (not recommended, but may be suitable if we're not comfortable with the forking model).

4. A new  `private` repository type becomes possible. These repositories are only visible and editable when a person or team is explicitly added to the repository. This is useful for personal lab projects or things that shouldn't be shared outside a team for whatever reason.

## Things that won't change

- The "innersource" model, encouraging knowledge sharing, code visibility and changes from around the organisation will still be encouraged. If this change introduces recurring friction, we can/should resolve that through appropriate assignment of teams to repositories rather than accepting the friction.

- Teams will still work on their day-to-day projects in the same way.

- Shared Services will continue to be able to contribute to Housing Products and Targeted Services repositories, as they already have the `write` permission on those repositories.