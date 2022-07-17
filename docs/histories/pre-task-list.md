---
layout: post
includeInBreadcrumbs: true
order: 1
title: Pre task-list
description: A series of prototype screenshots, including summary page text decoration varinats
eleventyNavigation:
  key: Pre task-list
  parent: Histories
aside:
  title: NCTS P5 prototype
  content: |
    Username:  prototype
    Password:  thisisabadpassword

    The Model is behind a VPN, 
    only HMRC staff can access
related:
  sections:
    - items:
        - text: Prototype link
          href: https://ctc-trader-p5-prototype.herokuapp.com
        - text: Model link
          href: https://app.diagrams.net/#G15taz7Mp4fHI6uLJfiki2UtcY08oxmCby
---

## The start

This is the very start of a departure declaration, this is only 5 to 7 pages long but does affect how the sections ahead will ask for relevant information.

The prototype filters through a select of different offices of departures and applies branching based on the user selection.

This functionality does not come out of the box in the prototype kit or the design system, but proved essential, to simplify the whole user journey.

#### Screenshots

- A static homepage with links to varius journeys
  (A dashboard re-design is planned for Private Beta)

![A homepage](/assets/pre-task-list/homepage.png "The current homepage")
<br>

- A small mandatory journey for all the NCTS users
- This is appropriately branched with routes leading to different outcomes for the end to end journey.
- The Local Reference Number is the first step in this transactional service

![A text input](/assets/pre-task-list/lrn-input.png "The LRN input page")
<br>

- A single "Empty" error validation for enhanced usability testing

![An error message](/assets/pre-task-list/lrn-error.png "The LRN input page 'Empty' error validation")
<br>

- An accessible autocomplete with a select, again this is appropriately branched with routes leading to different outcomes for the end to end journey
- Behiavour screenshots

![A select field](/assets/pre-task-list/office-of-departure-1.png "The office of departures select field")
<br>

![A select field](/assets/pre-task-list/office-of-departure-2.png "The office of departures select field")
<br>

![A select field](/assets/pre-task-list/office-of-departure-3.png "The office of departures select field")
<br>

Two separate data groups of office are included in the `data.js` file: `officesGB` and `officesNI`. When the user selects one of the 3 NI offices they need to go down a different path. The code block below in the `routes.js` file has allowed this functionality.

```js
router.post("/office-of-departure", function (req, res) {
  const selectedOffice = req.session.data.officeOfDeparture;

  const officesNI = [
    "Belfast EPU XI000142",
    "Warrenpoint XI005160",
    "Larne XI005220",
  ];

  if (officesNI.includes(selectedOffice)) {
    res.redirect("procedure-type-xi");
  } else {
    res.redirect("procedure-type");
  }
});
```

- A radio group that was purposefully vertical, due to long content on the radio buttons
- This is routed and branches out to divergent paths

![A radio group](/assets/pre-task-list/procedure-type.png "The procedure type radio group")
<br>

- This is a dynamic radio group that can have 4 or 5 options depending on previous choises

![A radio group](/assets/pre-task-list/declaration-type.png "The declaration type radio group")
<br>

- This is an extra question that is only needed if the users select a specific combination of answers previously. Specifically an XI (Northern Ireland) office of departure, a 'normal' procedure type and a 'TIR' declaration type.

![A radio group](/assets/pre-task-list/tir-carnet.png "The extra question")
<br>

- In the end the users were shown a summary list with links to their answers and a warning that after confirming, they would not be able to amend these previous answers after this point.

![A radio group](/assets/pre-task-list/cya-paragraph.png "The first iteration of the CYA")
<br>

#### A pain point we discovered

In the end of the pre-task list of questions, you come to a summary page where the users are shown the answers [page](/histories/macro-interactions). they provided.
