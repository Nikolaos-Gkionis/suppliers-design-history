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

Users highlighted the repetition of information - they were adding the details of connected persons, then duplicating that information if the connected person was the subject of an exclusion. This process followed the policy instructions, but was not an ideal user journey.

We improved the journey by using the connected person as the ‘master’ and asking users to select the appropriate person. If a user wanted to add a person that wasn’t listed as the subject of an exclusion, we directed them towards adding them as a connected person first, then they could be selected, with only minor additional information required.

### Pre-Enhancement Challenges

Prior to this enhancement, the user had to add the details for each person that was the subject of an exclusion. This often duplicated information that had previously been given for the person in their role as a connected person:

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