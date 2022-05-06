# zenhub api evaluation

Below you can find the list of needed rest api calls in order to:
- get zenhub release id
- get issues from it
- create a github milestone
- assign issue to a milestone

the zenhub repo_id is **489076909**
this github repo is **zenhub-api-test**
this owner of github is **MV88**

## zenhub

### Request to get all releases (zenhub)

```curl
curl --location --request GET 'https://api.zenhub.com/p1/repositories/489076909/reports/releases?access_token=<ZENHUB_TOKEN>'
```

Response example
```json
[
    {
        "release_id": "Z2lkOi8vcmFwdG9yL1JlbGVhc2UvNzYyMjg",
        "title": "release beda",
        "description": "release beda",
        "start_date": "2022-05-05",
        "desired_end_date": "2022-05-13",
        "created_at": "2022-05-05T18:05:33Z",
        "closed_at": null,
        "state": "open"
    }
]
```
### Request to get all issues given a zenhub release (zenhub)

```curl
curl --location --request GET 'https://api.zenhub.com/p1/reports/release/Z2lkOi8vcmFwdG9yL1JlbGVhc2UvNzYyMjg/issues?access_token=<ZENHUB_TOKEN>'
```

Response example

```json
[
    {
        "repo_id": 489076909,
        "issue_number": 1
    },
    {
        "repo_id": 489076909,
        "issue_number": 2
    },
    {
        "repo_id": 489076909,
        "issue_number": 3
    }
]

```
## github

### Get milestones by owner-repo (github)

```curl
curl --location --request GET 'https://api.github.com/repos/mv88/zenhub-api-test/milestones' \
--header 'Accept: application/vnd.github.v3+json' \
--header 'Authorization: token <GITHUB_PAT_TOKEN>'
```

Response
```json
[
    {
        "url": "https://api.github.com/repos/MV88/zenhub-api-test/milestones/1",
        "html_url": "https://github.com/MV88/zenhub-api-test/milestone/1",
        "labels_url": "https://api.github.com/repos/MV88/zenhub-api-test/milestones/1/labels",
        "id": 7949569,
        "node_id": "MI_kwDOHSa4rc4AeU0B",
        "number": 1,
        "title": "v1.0.0",
        "description": null,
        "creator": {
            "login": "MV88",
            "id": 11991428,
            "node_id": "MDQ6VXNlcjExOTkxNDI4",
            "avatar_url": "https://avatars.githubusercontent.com/u/11991428?v=4",
            "gravatar_id": "",
            "url": "https://api.github.com/users/MV88",
            "html_url": "https://github.com/MV88",
            "followers_url": "https://api.github.com/users/MV88/followers",
            "following_url": "https://api.github.com/users/MV88/following{/other_user}",
            "gists_url": "https://api.github.com/users/MV88/gists{/gist_id}",
            "starred_url": "https://api.github.com/users/MV88/starred{/owner}{/repo}",
            "subscriptions_url": "https://api.github.com/users/MV88/subscriptions",
            "organizations_url": "https://api.github.com/users/MV88/orgs",
            "repos_url": "https://api.github.com/users/MV88/repos",
            "events_url": "https://api.github.com/users/MV88/events{/privacy}",
            "received_events_url": "https://api.github.com/users/MV88/received_events",
            "type": "User",
            "site_admin": false
        },
        "open_issues": 0,
        "closed_issues": 0,
        "state": "open",
        "created_at": "2022-05-06T07:49:13Z",
        "updated_at": "2022-05-06T07:49:13Z",
        "due_on": null,
        "closed_at": null
    }
]
```

### Create milestone (github)

```curl
curl --location --request POST 'https://api.github.com/repos/MV88/zenhub-api-test/milestones' \
--header 'Accept: application/vnd.github.v3+json' \
--header 'Authorization: token <GITHUB_PAT_TOKEN>' \
--header 'Content-Type: application/json' \
--data-raw '{
  "title": "v1.0.0",
  "state": "open"
}'
```

Response
```json
{
    "url": "https://api.github.com/repos/MV88/zenhub-api-test/milestones/1",
    "html_url": "https://github.com/MV88/zenhub-api-test/milestone/1",
    "labels_url": "https://api.github.com/repos/MV88/zenhub-api-test/milestones/1/labels",
    "id": 7949569,
    "node_id": "MI_kwDOHSa4rc4AeU0B",
    "number": 1,
    "title": "v1.0.0",
    "description": null,
    "creator": {
        "login": "MV88",
        "id": 11991428,
        "node_id": "MDQ6VXNlcjExOTkxNDI4",
        "avatar_url": "https://avatars.githubusercontent.com/u/11991428?v=4",
        "gravatar_id": "",
        "url": "https://api.github.com/users/MV88",
        "html_url": "https://github.com/MV88",
        "followers_url": "https://api.github.com/users/MV88/followers",
        "following_url": "https://api.github.com/users/MV88/following{/other_user}",
        "gists_url": "https://api.github.com/users/MV88/gists{/gist_id}",
        "starred_url": "https://api.github.com/users/MV88/starred{/owner}{/repo}",
        "subscriptions_url": "https://api.github.com/users/MV88/subscriptions",
        "organizations_url": "https://api.github.com/users/MV88/orgs",
        "repos_url": "https://api.github.com/users/MV88/repos",
        "events_url": "https://api.github.com/users/MV88/events{/privacy}",
        "received_events_url": "https://api.github.com/users/MV88/received_events",
        "type": "User",
        "site_admin": false
    },
    "open_issues": 0,
    "closed_issues": 0,
    "state": "open",
    "created_at": "2022-05-06T07:49:13Z",
    "updated_at": "2022-05-06T07:49:13Z",
    "due_on": null,
    "closed_at": null
}
```

### Assign milestone to issue (github)

use previous **number** of previous request to associate with milestone number in the body

```curl
curl --location --request POST 'https://api.github.com/repos/MV88/zenhub-api-test/issues/2' \
--header 'Accept: application/vnd.github.v3+json' \
--header 'Authorization: token <GITHUB_PAT_TOKEN>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "milestone": 1
}'
```

Response
```json
{
    "url": "https://api.github.com/repos/MV88/zenhub-api-test/issues/2",
    "repository_url": "https://api.github.com/repos/MV88/zenhub-api-test",
    "labels_url": "https://api.github.com/repos/MV88/zenhub-api-test/issues/2/labels{/name}",
    "comments_url": "https://api.github.com/repos/MV88/zenhub-api-test/issues/2/comments",
    "events_url": "https://api.github.com/repos/MV88/zenhub-api-test/issues/2/events",
    "html_url": "https://github.com/MV88/zenhub-api-test/issues/2",
    "id": 1227008023,
    "node_id": "I_kwDOHSa4rc5JIqgX",
    "number": 2,
    "title": "test issue 2",
    "user": {
        "login": "MV88",
        "id": 11991428,
        "node_id": "MDQ6VXNlcjExOTkxNDI4",
        "avatar_url": "https://avatars.githubusercontent.com/u/11991428?v=4",
        "gravatar_id": "",
        "url": "https://api.github.com/users/MV88",
        "html_url": "https://github.com/MV88",
        "followers_url": "https://api.github.com/users/MV88/followers",
        "following_url": "https://api.github.com/users/MV88/following{/other_user}",
        "gists_url": "https://api.github.com/users/MV88/gists{/gist_id}",
        "starred_url": "https://api.github.com/users/MV88/starred{/owner}{/repo}",
        "subscriptions_url": "https://api.github.com/users/MV88/subscriptions",
        "organizations_url": "https://api.github.com/users/MV88/orgs",
        "repos_url": "https://api.github.com/users/MV88/repos",
        "events_url": "https://api.github.com/users/MV88/events{/privacy}",
        "received_events_url": "https://api.github.com/users/MV88/received_events",
        "type": "User",
        "site_admin": false
    },
    "labels": [],
    "state": "open",
    "locked": false,
    "assignee": null,
    "assignees": [],
    "milestone": {
        "url": "https://api.github.com/repos/MV88/zenhub-api-test/milestones/1",
        "html_url": "https://github.com/MV88/zenhub-api-test/milestone/1",
        "labels_url": "https://api.github.com/repos/MV88/zenhub-api-test/milestones/1/labels",
        "id": 7949569,
        "node_id": "MI_kwDOHSa4rc4AeU0B",
        "number": 1,
        "title": "v1.0.0",
        "description": null,
        "creator": {
            "login": "MV88",
            "id": 11991428,
            "node_id": "MDQ6VXNlcjExOTkxNDI4",
            "avatar_url": "https://avatars.githubusercontent.com/u/11991428?v=4",
            "gravatar_id": "",
            "url": "https://api.github.com/users/MV88",
            "html_url": "https://github.com/MV88",
            "followers_url": "https://api.github.com/users/MV88/followers",
            "following_url": "https://api.github.com/users/MV88/following{/other_user}",
            "gists_url": "https://api.github.com/users/MV88/gists{/gist_id}",
            "starred_url": "https://api.github.com/users/MV88/starred{/owner}{/repo}",
            "subscriptions_url": "https://api.github.com/users/MV88/subscriptions",
            "organizations_url": "https://api.github.com/users/MV88/orgs",
            "repos_url": "https://api.github.com/users/MV88/repos",
            "events_url": "https://api.github.com/users/MV88/events{/privacy}",
            "received_events_url": "https://api.github.com/users/MV88/received_events",
            "type": "User",
            "site_admin": false
        },
        "open_issues": 2,
        "closed_issues": 0,
        "state": "open",
        "created_at": "2022-05-06T07:49:13Z",
        "updated_at": "2022-05-06T08:08:58Z",
        "due_on": null,
        "closed_at": null
    },
    "comments": 0,
    "created_at": "2022-05-05T18:04:21Z",
    "updated_at": "2022-05-06T08:08:58Z",
    "closed_at": null,
    "author_association": "OWNER",
    "active_lock_reason": null,
    "body": null,
    "closed_by": null,
    "reactions": {
        "url": "https://api.github.com/repos/MV88/zenhub-api-test/issues/2/reactions",
        "total_count": 0,
        "+1": 0,
        "-1": 0,
        "laugh": 0,
        "hooray": 0,
        "confused": 0,
        "heart": 0,
        "rocket": 0,
        "eyes": 0
    },
    "timeline_url": "https://api.github.com/repos/MV88/zenhub-api-test/issues/2/timeline",
    "performed_via_github_app": null
}
```