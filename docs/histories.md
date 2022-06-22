---
layout: collection
includeInBreadcrumbs: true
order: 2
title: Histories
description: A design history of Phase 5 Discovery and Alpha. It features posts that describe the development of new features, iterations of existing ones.
paginationHeading: Design History
pagination:
  data: histories
  size: 10
histories:
  - url: "/histories/phase-4"
    data:
      date: 2021-08-17
      title: Phase 4 design
      description: Here are the prototype pages from phase 4.
  - url: "/histories/phase-5-discovery"
    data:
      date: 2021-09-08
      title: Phase 5 discovery
      description: Reviewing the phase 5 discovery for NCTS.
  - url: "/histories/phase-4"
    data:
      date: 2021-08-17
      title: Phase 4 design
      description: Here are the prototype pages from phase 4.
  - url: "/histories/phase-5-discovery"
    data:
      date: 2021-09-08
      title: Phase 5 discovery
      description: Reviewing the phase 5 discovery for NCTS.
  - url: "/histories/phase-4"
    data:
      date: 2021-08-17
      title: Phase 4 design
      description: Here are the prototype pages from phase 4.
  - url: "/histories/phase-5-discovery"
    data:
      date: 2021-09-08
      title: Phase 5 discovery
      description: Reviewing the phase 5 discovery for NCTS.
aside:
  title: NCTS P5 prototype
  content: |
    Username: prototype
    Password: thisisabadpassword
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
