---
layout: collection
includeInBreadcrumbs: true
order: 2
title: Design histories
description: Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Praesent sagittis ornare diam id mollis.
eleventyNavigation:
  key: Histories
paginationHeading: Design Histories
pagination:
  data: histories
  size: 10
histories:
  - url: "/histories/routes"
    data:
      date: 2022-09-21
      title: Routes sub-journey
      description: A complex sub-journey with many variable paths and dependencies.
  - url: "/histories/dashboard-design"
    data:
      date: 2022-08-23
      title: Dashboard design
      description: A/B testing dashboard variants for save and retrieve functionality.
  - url: "/histories/validation"
    data:
      date: 2022-07-15
      title: Validation
      description: Should prototypes have validation?
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
