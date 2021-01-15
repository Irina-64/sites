---
title: React Server Components Announcement Notes
date: 2021-01-14
description: Three weeks after the React Server Components event, I finally sat down to learn what everything was about. Here are my initial notes…
layout: layouts/post.njk
---

Three weeks after the announcement of React Server Components, I finally sat down [with friends](https://twitter.com/chantastic/status/1349710359049940992?s=20) to watch the event.

These notes are just a few ideas and links I'd like to hold onto for my next pass thru the demo app.

## Announcement

[Announcement Post](https://reactjs.org/blog/2020/12/21/data-fetching-with-react-server-components.html)
<br />

[server-components-demo](https://github.com/reactjs/server-components-demo)

<iframe width="640" height="360" src="https://www.youtube.com/embed/TQQPAU21ZUw" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Discussion

Real-time [discussion in Discord](https://discord.com/channels/105756917887950848/755466593261322301/799335521787838494) with the React Podcast community.

## New packages

| Name          | Use                  | Source                                                                       | Package                                                                |
| :------------ | :------------------- | :--------------------------------------------------------------------------- | :--------------------------------------------------------------------- |
| `react-fetch` | `fetch` wrapper      | [GitHub](https://github.com/facebook/react/tree/master/packages/react-fetch) | [npm](https://www.npmjs.com/package/react-fetch)                       |
| `react-fs`    | `Postgres` wrapper   | [GitHub](https://www.npmjs.com/package/react-fs)                             | [npm](https://github.com/facebook/react/tree/master/packages/react-fs) |
| `react-pg`    | Node.js `fs` wrapper | [GitHub](https://www.npmjs.com/package/react-pg)                             | [npm](https://github.com/facebook/react/tree/master/packages/react-pg) |

## Demo App Notes

[Matt Sutkowski](https://gist.github.com/msutkowski) lead our Discord discussion group thru the demo.  
He documented his findings and first impressions [in this gist](https://gist.github.com/msutkowski/90c90d04474ce51d0e56e96bb21e980d).

### Complications

The demo app is NOT straight forward.  
I think this is related to two things:

- It's a full stack application
- It's trying desperately not to use libraries like [react-router](https://reactrouter.com) for routing

At this point, this demo feels geared toward meta-frawork creators, e.g., [Next.js](https://nextjs.org) and [Remix](https://remix.run)

### Setup

Because this is a full stack app, you'll need to setup a full stack environment.  
The steps are detailed in the [Setup](https://github.com/reactjs/server-components-demo#setup) and [DB Setup](https://github.com/reactjs/server-components-demo#db-setup) sections of the [README](https://github.com/reactjs/server-components-demo).

I'll re-iterate a comple points with some added practical details.

#### Node

You need `node >= 14.9.0`.

If you need to manage different versions of Node.js, consider [nvm](https://github.com/nvm-sh/nvm).  
It's what I use to jump between projects with different `node` requirements.

With nvm, run `nvm install 14` in the project root and you're good to go.

#### Docker

You need `docker-compose` to run this `server-components-demo`.  
Find [platform-specific instructions here](https://docs.docker.com/compose/install/).

On a mac, the quickest path to a demo is installing the [Docker Desktop Mac App](https://docs.docker.com/docker-for-mac/install/) — which includes `docker-compose`.

#### Postgres DB

_(if you don't want to endure this step, [Rodrigo Pombo](@pomber) has a [DB-less fork of `server-components-demo`](https://github.com/pomber/server-components-demo/))_

[DB Setup] instructions are [here](https://github.com/reactjs/server-components-demo#db-setup).

[Platform-specefic installation instructions here](https://wiki.postgresql.org/wiki/Detailed_installation_guides).  
On a mac, the quickest path to a demo is installing [Postgress.app](https://postgresapp.com).

Personally, I manage a Postgres installation with [Homebrew](https://brew.sh).

- (with `brew` command available)
  — installed Postgres with `brew install postgresql`
  — run `brew services start postgres` to start the Postgres daemon
  — run `brew services stop postgres` to stop the Postgres daemon

With Postgres setup, follow the [remaining istructions](https://github.com/reactjs/server-components-demo#db-setup) to setup and seed a database for you demo app.

## Location oddities

Something to keep in mind is that `navigate` and `location` have nothing to do with url.

The user's "location" in the app is held in state and communicated as a query parameter to server-side requests — to provide the correct data.

This clearly a void that would be filled by a meta-framework and the implementation in the DEMO is a mimimum-required effort to prove the concept.  
This is not what real code would look like.
Same sentiment for inline Postgres queries in `.server.js` components.

## Deployable demos

- [verces/react-server-components](https://github.com/vercel/next-server-components)
- [netlify/server-components-demo](https://github.com/netlify/react-server-components-demo)

## First impressions

All things considered, this is an enjoyable experiment.  
Clearly this isn't intended for public consumption yet but I love seeing the concepts shared openly with a workable public demo.