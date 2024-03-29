# API Scopes

There are two distinct types of scopes, user scopes and client scopes.

- User scopes and client scopes. User scopes are stored in the `users` table and are applied specifically after authorizing via osu!, through the website.
- Client scopes are authorized to third-party OAuth clients. Typically, these clients have a broader range of possibilities than user scopes. As of right now, client scopes do not support any user-specific endpoints such as `/me` or `/dashboard`, but they do have access to the endpoints that those functions rely on, such as `/stats`.

Currently, endpoints are *not* documented publicly, so this knowledge is relatively useless without a deep understanding of how the API works.

Note: Scopes indicated as default are not stored as a scope in the database, they are applied directly when making the encrypted access tokens.

## User Scopes

The following scopes are possible to grant to users. They are listed in order of least to most privileged. Multiple scopes must be granted individually - i.e. a user with only `Verifier` cannot do anything more than verify matches.

As the website is currently closed to the public, both the current state of the default role and the intended state are documented.

- `user` *default*: No access.
- `whitelist`: Grants access to the website during the whitelist-only pre-alpha feedback phase.
- `user` *default (after pre-alpha phase)*: Grants general user access to typical endpoints such as `/leaderboard`, `/me`, `/dashboard`, etc. Made available to all users by default.
- `submit`: Allows users to submit matches using the match submission form.
- `verifier`: Allows users with `Submit` to force mark these matches as `verified`, bypassing the manual approval waiting period for normal submissions.
- `admin`: Allows users access to the admin panel, and generally access to all read/write functions made available on the website.

## Client Scopes

The following scopes are made available to third-party OAuth clients.

- `client` *default*: Has access to publicly available data.
- `system`: Reserved specifically for the `otr-processor` tool. Grants full read/write API access.