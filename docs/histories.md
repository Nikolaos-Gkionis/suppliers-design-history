---
layout: collection
includeInBreadcrumbs: true
order: 2
title: Design histories
description: Design histories are posts about the evolution and the design decisions of the service. They are smaller than case studies and provide a snapshot on a section of the whole service.
eleventyNavigation:
  key: Histories
paginationHeading: Design Histories
pagination:
  data: histories
  size: 10
histories:
  - url: "/histories/start"
    data:
      date: 2023-10-21
      title: A New Start page
      description: Creating a 'Start a service' page for the Suppliers information service.
  - url: "/histories/replicator"
    data:
      date: 2023-10-22
      title: Address replicator (Basic Information)
      description: Enhancement to enable address reuse, thus saving time and improving accuracy.
  - url: "/histories/hint"
    data:
      date: 2023-10-23
      title: The Role of Hint Text
      description: The importance of providing additional contextual information, often referred to as Hint Text.
  - url: "/histories/share"
    data:
      date: 2023-10-24
      title: The Ultimate goal
      description: The whole purpose of this service is to allow suppliers to share their core data, how are we improving this goal.
related:
  sections:
    - items:
        - text: Latest Prototype link
          href: https://si-prototype-616667192c06.herokuapp.com/
tags:
  - homepage
---

{% for page in collections["histories"] %}

- [{{ page.data.title }}]({{ page.url | url }}) – {{ page.data.description }}

{% endfor %}
