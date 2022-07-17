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

The prototype includes an add/remove functionality in order to allow for more in depth research and testing.

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

#### The add another feature

At the end of the journey the user is presented with an option to add another guarantee to their declaration, this can go up to 9 different guarantees and then the user needs to remove one before adding another.

![A screenshot](/assets/guarantee/07.png "A screenshot of the guarantee sub-journey")
<br>

#### A D.R.Y (A Do not Repeat Yourself)

The code required to add and remove guarantees from the declaration. This code builds an array and indexes the guarantee, every time the user adds another guarantee, the maximum is set to nine. This code will be made part of every other add another pattern required through the prototype in the Routes, Transport, House Consignments and so on.

```js
router.get("/:index/remove-guarantee", function (req, res) {
  res.render(path.resolve(__dirname, "remove-guarantee"));
});

router.post("/:index/remove-guarantee", function (req, res) {
  let removeGuarantee = req.session.data.removeGuarantee;
  const guarantees = req.session.data.guaranteeArray || [];

  if (removeGuarantee == "Yes" && guarantees.length) {
    const deleteIndex = req.params.index - 1;
    const maxIndex = guarantees.length || 0;

    if (deleteIndex <= maxIndex) {
      guarantees.splice(deleteIndex, 1);

      req.session.data.guaranteeArray = guarantees;
      req.session.data.guaranteeCount = guarantees.length;
    }
  }

  res.redirect("../add-another-guarantee");
});

router.get("/:index/check-answers", function (req, res) {
  const data = req.session.data;
  const index = parseInt(req.params.index);
  const guarantees = data.guaranteeArray || [];

  if (!guarantees.length) {
    return res.redirect("../add-another-guarantee");
  }

  const guarantee = guarantees[req.params.index - 1] || {};

  req.session.data = {
    ...data,
    ...guarantee,
    editGuarantee: index,
  };

  res.redirect("../check-answers");
});

router.post("/check-answers", function (req, res) {
  const data = req.session.data;
  const guarantees = data.guaranteeArray || [];

  const guarantee = {
    guaranteeType: data.guaranteeType,
    guaranteeReference: data.guaranteeReference,
    liabilityAmount: data.liabilityAmount,
    accessCode: "****",
  };

  if (data.editGuarantee) {
    guarantees[data.editGuarantee - 1] = guarantee;
  } else {
    guarantees.push(guarantee);
    data.guaranteeArray = guarantees;
    data.guaranteeCount = guarantees.length;
  }

  delete data.editGuarantee;

  res.redirect("add-another-guarantee");
});

router.post("/add-another-guarantee-route", function (req, res) {
  var sessionData = req.session.data;
  var guaranteeArray = sessionData.guaranteeArray || [];
  var guarantee = {
    id: guaranteeArray.length + 1,
    guarantee: sessionData.guaranteeType,
  };
  guaranteeArray.push(guarantee);
  sessionData.guaranteeArray = guaranteeArray;
  sessionData.guaranteeCount = guaranteeArray.length;
  res.redirect("add-another-guarantee");
});

router.post("/guarantee-added-tir", function (req, res) {
  res.redirect("../task-list-3");
});

router.post("/add-another-guarantee", function (req, res) {
  delete req.session.data.editGuarantee;

  if (req.session.data.addAnotherGuarantee == "Yes") {
    res.redirect("guarantee-type");
  } else {
    res.redirect("../task-list");
  }
});

router.post("/add-another-guarantee", function (req, res) {
  delete req.session.data.editGuarantee;

  if (req.session.data.guaranteeCount == "9") {
    res.redirect("../task-list");
  } else {
    res.redirect("guarantee-type");
  }
});
```

#### The declaration summary

At the end of the journey the user is then taken back to the declaration summary where they can see that they have completed this section.

![A screenshot](/assets/guarantee/08.png "A screenshot of the declaration summary")
<br>
