---
title: Cycle Activation
sidebar: cyclr_sidebar
permalink: cycle-activation.html
tags: [installing]
---

# Cycle Activation #

_**When a cycle is installed in an account they are in a Paused state and must be activated to before any step requests will be processed.**_

When a Cycle has been installed and all of it’s prerequisites have been provided, the cycle can be activated like below:

    POST /v1.0/cycles/{Cycle ID}/activate
    Authorization Bearer 0000000000000000000000000000000000000000000000000000000000000000

    {
        "StartTime": "2018-01-01T00:00:00Z",
        "Interval": 360,
        "RunOnce": false
    }

<table>
    <tr>
        <th>StartTime</th>
        <td>Optional, the time for the Cycle to start (UTC)</td>
    </tr>
    <tr>
        <th>Interval</th>
        <td>The frequency that the Cycle should run at, ignored if first step is webhook</td>
    </tr>
    <tr>
        <th>RunOnce</th>
        <td>Optional, set to true for the Cycle to auto paused after the first run</td>
    </tr>
</table> 

Response:

    200 OK

The Cycle will then run at StartTime and run every Interval (seconds), unless RunOnce is true, in which case the Cycle will run one time at StartTime (or after StartTime if triggered by a webhook).