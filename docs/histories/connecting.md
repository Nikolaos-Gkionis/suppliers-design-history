---
layout: post
includeInBreadcrumbs: true
order: 1
description: How we connected separate sections and data to reduce duplication and improve the service overall user experience.
eleventyNavigation:
  key: Postcode
  parent: Histories
aside:
  title: SI Version 4 prototype
  content: |
    Password:  V4-Proto
related:
  sections:
    - items:
        - text: Prototype link
          href: https://suppliers-v4-proto-8e2c4514d095.herokuapp.com/
---


## Enhancing Data Flow Across Sections

### Addressing User Feedback and Improving User Journey

In response to user feedback highlighting concerns about the overwhelming nature of repeated information requests, a decision was made to enhance the prototype's functionality. The proposed solution involved implementing a mechanism to pass previously committed data from one section to another. This strategic decision was greenlit, and the team proceeded with the necessary improvements.

### Pre-Enhancement Challenges

Prior to this enhancement, the practice of passing data between pages was not unfamiliar, especially in GDS style prototypes where it was commonly employed for a 'Check your Answers' page. However, our unique use case presented a complex challenge. We needed to transmit details for an indefinite number of data sets, each comprising 9 variable types, 3 types of addresses, and a diverse data schema for each of the 9 types. The complexity made it nearly impossible to accurately calculate and bring the correct data set into subsequent sections.

The culmination of the user's journey, showing the count of connected persons added, was displayed on the 'Account Home' page. Subsequent pages, including the 'Mandatory Exclusions' section, required the user to make selections based on previously input data.

![Previous](/assets/connect/1.png)

![Previous](/assets/connect/2.png)

![Previous](/assets/connect/3.png)

![Previous](/assets/connect/4.png)

Repeating questions and additional address request pages followed, leading to a cascade of redundant content.

![Previous](/assets/connect/5.png)

![Previous](/assets/connect/6.png)

![Previous](/assets/connect/7.png)

![Previous](/assets/connect/8.png)

![Previous](/assets/connect/9.png)

All these redundant pages have now been rendered obsolete, resulting in a reduction of 4 pages in total.

The redesigned initial page now empowers users to declare 'none,' streamlining the process.

![Previous](/assets/connect/10.png)

Users only need to select a previously reported connected person, the supplier, or choose to go back to submit details for a not-yet-declared connected person.

![Previous](/assets/connect/11.png)

The only remaining question from the previous, more extended journey is related to the email.

![Previous](/assets/connect/12.png)

The subsequent pages remain unchanged.

![Previous](/assets/connect/13.png)
![Previous](/assets/connect/14.png)
![Previous](/assets/connect/15.png)

Additionally, at the 'add more' pattern towards the end of this journey, two objects from the array are brought back to better separate different exclusions as their numbers grow.

![Previous](/assets/connect/16.png)

### User Testing and Validation

Following the implementation of data passing to connect separate sections, comprehensive user testing will be conducted to assess its effectiveness and gather additional feedback. The team anticipates that the results will affirm the positive reception of this new feature among users.

### Conclusion

The introduction of these design changes in this sprint serves as a foundation for further improvements and guides the ongoing enhancement of this service to meet user needs. Similar enhancements have also been incorporated into the 'Discretionary Exclusions' journey, resulting in the removal of a total of 8 pages.

<a href="/histories" class="govuk-back-link">Back</a>