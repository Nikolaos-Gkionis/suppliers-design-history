---
layout: post
includeInBreadcrumbs: true
order: 6
description: The single biggest pain point was the 'Connected Persons' part of the journey, 100% of the users struggled in some way.
eleventyNavigation:
  key: Complexity
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

## Dealing with complexity 

The Connected persons section of the users journey had 14 out of 14 participants requiring more clarity. Ranging from not understanding exactly what was requested from them to not understanding what it meant as a phrase at all. The team had wrongly presupposed that the suppliers, as subject matter experts, would completely comprehend the definition and select the appropriate radio selection from the 9 options provided.

### The problem space

Moreover, once a user had selected one of the following 9 options they faced a series of input field questions relevant to the information required by legislation for them to declare. This also decreased user clarity and increased time spent in the sub-journey and the users had a negative view of this section overall.

**Before the Enhancement**

![Before Enhancement](/assets/complexity/2.png)

![Before Enhancement](/assets/complexity/3.png)

![Before Enhancement](/assets/complexity/4.png)

### Working with policy

In an effort to better understand the policy intend, the content definitions and the possible paths the users should take the team worked on providing a conditional logic model that would then inform the prototype to increase usability and allow the team to focus on dealing with the complex policy requirements in a way that enables the users, rather than frustrates them.

![The model](/assets/complexity/1.png)

### Increasing clarity

Furthermore, hint text was provided to increase the users understanding and after 2 boolean clarification questions the users will face a smaller set of options relevant to their specific circumstances.

**After the Enhancement**

![After Enhancement](/assets/complexity/5.png)

![After Enhancement](/assets/complexity/6.png)

### Next steps

In the second round of research we believe that this approach will benefit the service by providing a better understanding of the required information.

<a href="/histories" class="govuk-back-link">Back</a>