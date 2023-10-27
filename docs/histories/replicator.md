---
layout: post
includeInBreadcrumbs: true
order: 2
title: Address replicator 
description: Enhancement to enable address reuse, thus saving time and improving accuracy.
eleventyNavigation:
  key: Replicator
  parent: Histories
aside:
  title: SI Version 2 prototype
  content: |
    Password:  SI-V2
related:
  sections:
    - items:
        - text: Prototype link
          href: https://si-prototype-v2-28b848ff1dde.herokuapp.com/
---

#### Reason behind change 

User Feedback on Prototype Version 1.0 was noted, and summarised as follows:

Users are requesting a feature that allows them to easily reuse addresses they have previously inputted within the user journey. This would streamline the process of filling out forms by reducing the need to type out the same address information multiple times.

#### Description

The team redesigned the prototype where users were asked to enter the registered and postal addresses as follows:

To improve the user experience and address feedback provided, an additional screen was added in order to streamline the process of filling out forms by reducing the need to type out the same address information multiple times.
Prior to the user being asked to enter their postal address, a newly added screen enabled users to re-use the previously entered Registered Address value, before being asked to enter the Postal Address values manually.

#### Screenshots

The Screen for entering postal address prior to enhancement was not offering an address reuse option

- A screenshot of the Suppliers' address in the prototype

![A screenshot](/assets/replicator/1.png "A screenshot of the prototype")
<br>

Following enhancement, the prototype screens for entering postal address  offered an address reuse option

- A screenshot of the address replicator in the prototype

![A screenshot](/assets/replicator/2.png "A screenshot of the prototype")
<br>

The user then skipped the address form and the boolean question and simply came back to the Basic Information page with the contact address populated with the previously entered address.

- A screenshot of the Basic information with the address repeated.

![A screenshot](/assets/replicator/3.png "A screenshot of the prototype")
<br>