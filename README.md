hubot-pubsub
============

PubSub notification system for [Hubot](https://github.com/github/hubot)

[![Build Status](https://travis-ci.org/spajus/hubot-pubsub.png?branch=master)](https://travis-ci.org/spajus/hubot-pubsub)

![hubot-pubsub demo](https://dl.dropboxusercontent.com/u/176100/opensource/hubot-pubsub.gif)

## Possibilities

`hubot-pubsub` allows you to build a simple, yet powerful monitoring / notification system using your corporate chat
(Campfire, HipChat, IRC, Jabber / XMPP or even Skype). Simply subscribe events in appropriate chat rooms and publish
info about these events via HTTP calls when they happen.

## Installing

Add dependency to Hubot's `package.json`:
```json
{
  ...
  "dependencies": {
    ...
    "hubot-pubsub": "git://github.com/hubot-scripts/hubot-example.git#master"
  }
}
```

Include package in Hubot's `external-scripts.json`:
```json
["hubot-example"]
```

## Configuration

    HUBOT_SUBSCRIPTIONS_PASSWORD   # Optional password for protecting HTTP API calls

## Commands

    hubot subscribe <event>        # subscribes current room to event
    hubot unsubscribe <event>      # unsubscribes current room from event
    hubot unsubscribe all events   # unsubscribes current room from all events
    hubot subscriptions            # show subscriptions of current room
    hubot all subscriptions        # show all existing subscriptions
    hubot publish <event> <data>   # triggers event

## HTTP API

### GET /publish

    GET /publish?event=<event>&data=<text>[&password=<password>]


### POST /publish

    POST /publish

  - Content-Type: `application/json`
  - Body: `{ "password": "optional", "event": "event", "data": "text" }`


### Issues

- HTTP password based security is weak - don't use it in public network to publish events with sensitive data
