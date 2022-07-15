---
layout: collection
includeInBreadcrumbs: true
order: 2
title: Design history
description: A design history of Phase 5 Discovery and Alpha. It features posts that describe the development of new features, iterations of existing ones.
eleventyNavigation:
  key: Histories
paginationHeading: Design History
pagination:
  data: histories
  size: 10
histories:
  - url: "/histories/macro-interactions"
    data:
      date: 2022-07-14
      title: Macro interactions
      description: A series of different approaches to a single user problem.
  - url: "/histories/house-consignments"
    data:
      date: 2022-07-07
      title: House consignments
      description: Exploring our riskiest assumption.
  - url: "/histories/guarantee"
    data:
      date: 2022-07-01
      title: Guarantee
      description: One of our smallest sub-journeys with a lot of dependencies.
  - url: "/histories/trader-details"
    data:
      date: 2022-06-30
      title: Trader details
      description: The new phase 5 trader details journey.
  - url: "/histories/pre-task-list"
    data:
      date: 2022-06-21
      title: Pre task-list
      description: The first step every user takes to complete a departure declaration.
  - url: "/histories/the-model"
    data:
      date: 2022-05-15
      title: The Model
      description: A model of information dependencies and branching used as a guide to an accurate fully functional prototype.
  - url: "/histories/map"
    data:
      date: 2022-06-10
      title: The Map
      description: Ecosystem and Service landscape for phase 5.
aside:
  title: NCTS P5 prototype
  content: |
    Username:  prototype
    Password:  thisisabadpassword
related:
  sections:
    - items:
        - text: Prototype link
          href: https://ctc-trader-p5-prototype.herokuapp.com/
tags:
  - homepage
---

{% for page in collections["histories"] %}

- [{{ page.data.title }}]({{ page.url | url }}) – {{ page.data.description }}

{% endfor %}
