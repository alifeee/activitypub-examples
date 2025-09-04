# ActivityPub JSON examples

Examples of ActivityPub Objects from various sites implementing the protocol. The sites used are:

- <https://events.sheffield.alifeee.co.uk/events>
- <https://mastodon.social/@alifeee/>
- <https://ramblingreaders.org/user/alifeee/>

Then, in each folder, there is also a (manually) created "Movary" file.

(this is part of <https://github.com/leepeuker/movary/issues/686>)

most `curl` use the alias:

```bash
alias apcurl='apcurl=curl -H "Accept: application/ld+json, application/activity+json"'
```

## .well-known

### hostmeta

```bash
mkdir -p .well-known/host-meta
curl https://events.sheffield.alifeee.co.uk/.well-known/host-meta > .well-known/host-meta/activitybot.xml
curl https://mastodon.social/.well-known/host-meta > .well-known/host-meta/mastodon.xml
curl https://ramblingreaders.org/.well-known/host-meta > .well-known/host-meta/bookwyrm.xml
```

### webfinger

```bash
mkdir .well-known/webfinger
apcurl "https://events.sheffield.alifeee.co.uk/.well-known/webfinger?resource=acct:events@events.sheffield.alifeee.co.uk" \
  > .well-known/webfinger/activitybot.json
apcurl "https://mastodon.social/.well-known/webfinger?resource=acct:alifeee@mastodon.social" \
  > .well-known/webfinger/mastodon.json
apcurl "https://ramblingreaders.org/.well-known/webfinger?resource=acct:alifeee@ramblingreaders.org" \
  > .well-known/webfinger/bookwyrm.json
```

### nodeinfo

```bash
mkdir .well-known/nodeinfo
curl https://events.sheffield.alifeee.co.uk/.well-known/nodeinfo > .well-known/nodeinfo/activitybot.json
curl https://mastodon.social/.well-known/nodeinfo > .well-known/nodeinfo/mastodon.json
curl https://ramblingreaders.org/.well-known/nodeinfo > .well-known/nodeinfo/mastodon.json
mkdir nodeinfo
curl https://events.sheffield.alifeee.co.uk/nodeinfo/2.1 > nodeinfo/activitybot.json
curl https://mastodon.social/nodeinfo/2.0 > nodeinfo/mastodon.json
curl https://ramblingreaders.org/nodeinfo/2.0 > nodeinfo/bookwyrm.json
```

## Actor

```bash
mkdir Actor
apcurl https://events.sheffield.alifeee.co.uk/@events > Actor/activitybot.json
apcurl https://mastodon.social/@alifeee > Actor/mastodon.json
apcurl https://ramblingreaders.org/user/alifeee > Actor/bookwyrm.json
```

## Outbox

```bash
mkdir Outbox
apcurl https://events.sheffield.alifeee.co.uk/outbox > Outbox/activitybot.json
apcurl https://mastodon.social/users/alifeee/outbox > Outbox/mastodon.json
apcurl "https://mastodon.social/users/alifeee/outbox?page=true" > Outbox/mastodon_1.json
apcurl https://ramblingreaders.org/user/alifeee/outbox > Outbox/bookwyrm.json
apcurl "https://ramblingreaders.org/user/alifeee/outbox?page=1" > Outbox/bookwyrm_1.json
```

## Note

```bash
apcurl https://events.sheffield.alifeee.co.uk/posts/https:__www.welcometosheffield.co.uk_content_events_warrington-runcorn-new-town-development-programme_.json > Note/activitybot.json 
apcurl https://mastodon.social/users/alifeee/statuses/115136907246668600 > Note/mastodon.json
apcurl https://ramblingreaders.org/user/alifeee/comment/889707 > Note/bookwyrm.json
```

## Followers

```bash
apcurl https://events.sheffield.alifeee.co.uk/followers > Followers/activitybot.json
apcurl "https://events.sheffield.alifeee.co.uk/followers?page=1" > Followers/activitybot_1.json
apcurl https://mastodon.social/@alifeee/followers > Followers/mastodon.json
apcurl https://ramblingreaders.org/user/alifeee/followers > Followers/bookwyrm.json # I think this is broken :S
apcurl https://ramblingreaders.org/user/alifeee/followers?page=1 > Followers/bookwyrm_1.json
```

## Following

```bash
apcurl https://events.sheffield.alifeee.co.uk/following > Following/activitybot.json
apcurl "https://mastodon.social/users/alifeee/following" > Following/mastodon.json
apcurl "https://mastodon.social/users/alifeee/following?page=1" > Following/mastodon_1.json
apcurl "https://ramblingreaders.org/user/alifeee/following" > Following/bookwyrm.json # this is also broken
apcurl "https://ramblingreaders.org/user/alifeee/following?page=1" > Following/bookwyrm_1.json
```

## (bookwyrm specific) Edition/Author/Work

```bash
apcurl https://ramblingreaders.org/author/47 > Author/bookwyrm.json
apcurl https://ramblingreaders.org/book/219 > Edition/bookwyrm.json
apcurl https://ramblingreaders.org/book/218 > Work/bookwyrm.json
```
