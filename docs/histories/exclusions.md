---
layout: post
includeInBreadcrumbs: true
order: 6
description: The decision to use one pattern of design over another, in order to align with policy intent.
eleventyNavigation:
  key: Exclusions
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

## Designing with the outcome in mind

The Exclusions, both Mandatory and Discretionary are a multitude of fields that τhe policy intend requires the users to physically state via selecting yes or no, which if any exclusions need to be applied to each supplier. The initial design allowed the user to select only one, or a few checkboxes and therefore not explicitly state whether they as a supplier have committed a crime that needs an exclusion.

### The problem space

Moreover, this lack of behavioural anticipation would jeopardise the integrity of the data collected and assuming, or even worst collecting empty fields would put the service at a substantial legislative risk.

**Before the Enhancement**

![Before Enhancement](/assets/exclusions/1.png)

### Working with policy

In an effort to better understand the policy intend, the content definitions and the possible paths the users should take the team worked on providing a conditional logic model that would then inform the prototype to increase usability and allow the team to focus on dealing with the complex policy requirements in a way that enables the users, rather than frustrates them.


**After the Enhancement**

![After Enhancement](/assets/exclusions/2.png)

### Next steps

In the second round of research we believe that this approach will create the grounds for the intended behaviour to become manifest.

<a href="/histories" class="govuk-back-link">Back</a>