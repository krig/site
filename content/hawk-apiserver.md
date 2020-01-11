---
title: "Hawk API server"
date: 2020-01-11T16:14:12+01:00
Description: "Hawk API server"
Tags:
  - code
Categories:
  - whatever
---

My relationship with Go so far has been that it's a language that I don't love and
don't want to love, but which I find myself being effortlessly productive in, in
a way that I haven't experienced with a lot of other languages unless I have
years of experience with them.

The [Hawk API server](https://github.com/ClusterLabs/hawk-apiserver) is an
example of that. For the HA stack, we had been using `lighttpd` as the web
server for [Hawk](https://github.com/ClusterLabs/hawk), the web frontend for the
HA cluster stack.

Instead of switching to Apache which would cause headaches since we're also
hosting Apache has a cluster service, I started playing around with writing a
minimal web server in Go. At first my plan was to use some already existing web
server like Caddy, but I basically had a fully functional implementation working
already after my initial hack session.

Since then, the API server has gained a lot of interesting features. We use a
persistent connection to Pacemaker together with goroutines for each API call to
enable instant refresh of the web UI on cluster changes. I analyse the initial
bytes of the HTTP connection to see if it's HTTP or HTTPS, and respond to HTTP
with a redirect to HTTPS: That way, someone can type in the `IP:PORT` directly
into the browser location bar without adding `https://` in front and it'll still
work correctly.

