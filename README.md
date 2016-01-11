# gh-activity

#### **idea**

as an open source developer, i'm most proud of [my GitHub activity](https://github.com/ahdinosaur). yet the activity provided by GitHub is incomplete, showing only part of my overall contributions, [only providing detailed history up to a small window of recent events](https://github.com/ahdinosaur?tab=activity), and not highlighting most activity within orgs (where most of my activity happens). i wish [my website](http://dinosaur.is) provided a view into the full history, searchable and all, as a true display of my open source contributions.

here's an idea for how to achieve this. hey, anyone interested in implementing this?

## design

- use [gh-user-events](https://github.com/shinnn/gh-user-events) to get a live readable stream of [GitHub user events]
- pipe events in to a [levelup database](https://github.com/level/levelup).
  - use a [sublevel](https://www.npmjs.com/package/level-sublevel) for each type of event
  - use the timestamp as the key for each event
- provide server api that allows for streaming range queries using [multiplex-rpc](https://www.npmjs.com/package/multiplex-rpc)
- use [redux](http://redux.js.org) on client
  - connects over [websocket-stream](https://www.npmjs.com/package/websocket-stream)
  - render using [vdux](https://github.com/ashaffer/vdux)
    - [d3 time scales](https://github.com/mbostock/d3/wiki/Time-Scales)
    - [d3.scale](https://github.com/d3/d3-scale)
    - [d3.time](https://github.com/d3/d3-time)
