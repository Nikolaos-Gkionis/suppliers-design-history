---
layout: post
includeInBreadcrumbs: true
order: 1
title: Guarantee
description: The new phase 5 trader details journey.
eleventyNavigation:
  key: Guarantee
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

## A sub-journey

#### The dependencies

This is new section which allows the users to provide information about the guarantees they might need or want to attach to their departure declarations.

Users can view a list of different kind of guarantees, and add up to 9 per transit.

The prototype includes a add/remove functionality in order to allow for more in depth research and testing.

## Screenshots

![A screenshot](/assets/guarantee/01.png "A screenshot of the guarantee sub-journey")
<br>

The radio buttons lead to diveregent paths in the rest of the user journey, this can be achieved in the `routes.js` file.

```js
router.post("/guarantee-type", function (req, res) {
  const selectedGuarantee = req.session.data.guaranteeType;

  const guaranteeRadio = [
    "(0) Guarantee waiver",
    "(1) Comprehensive guarantee",
    "(2) Individual guarantee",
    "(4) Flat-rate voucher redirect(guarantee-reference)",
    "(5) Guarantee waiver",
    "(9) Individual guarantee with multiple usage",
    "(J) Guarantee not required for the journey",
  ];

  if (guaranteeRadio.includes(selectedGuarantee)) {
    res.redirect("guarantee-reference");
  } else if (
    selectedGuarantee == "(8) Guarantee not required for certain public bodies"
  ) {
    res.redirect("other-reference");
  } else if (
    selectedGuarantee ==
    "(3) Individual guarantee in cash or other means of payment"
  ) {
    res.redirect("other-reference-cash-deposit");
  } else {
    res.redirect("check-answers");
  }
});

router.post("/guarantee-type-xi", function (req, res) {
  const selectedGuarantee = req.session.data.guaranteeType;

  const guaranteeRadio = [
    "(0) Guarantee waiver",
    "(1) Comprehensive guarantee",
    "(2) Individual guarantee",
    "(4) Flat-rate voucher redirect(guarantee-reference)",
    "(5) Guarantee waiver",
    "(J) Guarantee not required for the journey",
  ];

  if (guaranteeRadio.includes(selectedGuarantee)) {
    res.redirect("guarantee-reference");
  } else {
    let guaranteeType = req.session.data.guaranteeType;

    if (
      guaranteeType == "(8) Guarantee not required for certain public bodies"
    ) {
      res.redirect("other-reference");
    } else if (
      guaranteeType ==
      "(3) Individual guarantee in cash or other means of payment"
    ) {
      res.redirect("other-reference-cash-deposit");
    } else res.redirect("check-answers");
  }
});

router.post("/guarantee-reference", function (req, res) {
  const selectedGuarantee2 = req.session.data.guaranteeType;

  const guaranteeRadio2 = [
    "(0) Guarantee waiver",
    "(1) Comprehensive guarantee",
    "(2) Individual guarantee",
    "(4) Flat-rate voucher redirect(guarantee-reference)",
    "(9) Individual guarantee with multiple usage (for CTC only)",
  ];

  if (guaranteeRadio2.includes(selectedGuarantee2)) {
    res.redirect("access-code");
  } else {
    res.redirect("check-answers");
  }
});
```

![A screenshot](/assets/guarantee/02.png "A screenshot of the guarantee sub-journey")
<br>

![A screenshot](/assets/guarantee/03.png "A screenshot of the guarantee sub-journey")
<br>

![A screenshot](/assets/guarantee/04.png "A screenshot of the guarantee sub-journey")
<br>

![A screenshot](/assets/guarantee/05.png "A screenshot of the guarantee sub-journey")
<br>

![A screenshot](/assets/guarantee/06.png "A screenshot of the guarantee sub-journey")
<br>

The code required to add and remove guarantees from the declaration.

![A code screenshot](/assets/guarantee/routes-2.png "A screenshot of the guarantee sub-journey code")
<br>

#### The add another feature

At the end of the journey the user is presented with an option to add anothe guarantee to their declaration, this can go up to 9 different guarantees and then the user needs to remove one before adding another.

![A screenshot](/assets/guarantee/07.png "A screenshot of the guarantee sub-journey")
<br>

#### The declaration summary

At the end of the journey the user is then taken back to the declaration summary where they can see that they have completed this section.

![A screenshot](/assets/guarantee/08.png "A screenshot of the declaration summary")
<br>
