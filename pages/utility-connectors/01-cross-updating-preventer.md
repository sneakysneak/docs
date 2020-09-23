---
title: Cross Updating Preventer
sidebar: cyclr_sidebar
permalink: cross-updating-preventer
tags: [utility-connector]
---

## Purpose

Many integrations are triggered when details of an updated record in one application is sent to a second application so as to keep the data in sync. There are occasions when this process needs to be bi-directional and this can result in an infinite cross-updating loop where A updates B, then B updates A and so on.

The Cyclr Cross Updating Preventer is designed to stop this.  It can be used to make sure that an inbound update to an application does not result in a return outbound update.
