---
layout: post
includeInBreadcrumbs: true
order: 1
description: Improving the user experience for the majority of the users
eleventyNavigation:
  key: Postcode
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

## Adding a UK postcode search functionality

### A Response to User Feedback

As our service prototype grew, we received valuable feedback from participants indicating that keying in addresses multiple times throughout the user journey was a pain point. They suggested implementing a postcode search functionality to streamline the process and improve the overall user experience.

### UX Designer's Perspective

From a UX design standpoint, simplifying the address input process was crucial for enhancing the user flow and reducing cognitive load. By introducing a postcode search feature, we aimed to minimize the number of steps required to enter an address, thereby improving the overall user experience. Additionally, we ensured that the postcode field was easily discoverable and accessible, further enhancing usability.

### UX Researcher's Perspective

From a UX research perspective, incorporating user feedback is essential for ensuring that our designs are user-centered and meet the needs of our target audience. The feedback regarding the address input process highlighted a potential area for improvement. By addressing this issue through a postcode search feature, we demonstrated our responsiveness to user feedback and our commitment to providing a seamless and enjoyable user experience.

### Providing the solution

n response to the user feedback, we implemented a postcode search functionality to streamline the address input process. We replaced the original fieldset of inputs with a simple postcode field input, allowing users to search for UK postcodes. This change significantly reduced the number of steps required to enter an address, making the process more efficient and user-friendly.

![Previous](/assets/postcode/1.png)

With a simple postcode field input, to allow the user to search for UK postcodes.

![Current](/assets/postcode/2.png)

The result is a list of radio buttons with the return addresses

![Current](/assets/postcode/3.png)

After the user selects an address the results are transferred to a CYA or wherever they are required in the journey.

![Current](/assets/postcode/5.png)

If the call returns no results the user is then taken to an address not found page, where the option to add the address manually is provided.

![Current](/assets/postcode/4.png)

### User Testing and validation

Following the implementation of the postcode search functionality, we will conduct further user testing to evaluate its effectiveness and gather additional feedback. The team expects the results to indicate that the new feature will be well-received by users, who appreciate the ease and convenience of searching for their addresses by postcode. Without loosing any accessibility or assisted digital users whilst looking for improvements.

### How you can do this for your service

To achieve the required functionality we used the Axios for API callbacks, and the OS Places API; first you need to install the API by simply running: 

```BASH 
npm install axios
```

In your terminal, in the root folder of your prototype, then you need to call the API at the top of your rotes.js file:

```JS
const express = require('express')
const router = express.Router()
const path = require('node:path')

// API
const axios = require('axios');

// Add your routes here - above the module.exports line
```

And here is the code that controls all three pages, the key is obfuscated for security:

```JS
router.post('/find-subject-uk-address', function (req, res) {

    var postcodeLookup = req.session.data['postcode']

    const regex = RegExp('^(([gG][iI][rR] {0,}0[aA]{2})|((([a-pr-uwyzA-PR-UWYZ][a-hk-yA-HK-Y]?[0-9][0-9]?)|(([a-pr-uwyzA-PR-UWYZ][0-9][a-hjkstuwA-HJKSTUW])|([a-pr-uwyzA-PR-UWYZ][a-hk-yA-HK-Y][0-9][abehmnprv-yABEHMNPRV-Y]))) {0,}[0-9][abd-hjlnp-uw-zABD-HJLNP-UW-Z]{2}))$');

    if (postcodeLookup) {

        if (regex.test(postcodeLookup) === true) {

            axios.get("https://api.os.uk/search/places/v1/postcode?postcode=" + postcodeLookup + "&key=" + "XXXXXXXXXXXXXXXXXXXXXXXX")
                .then(response => {
                    var addresses = response.data.results.map(result => result.DPA.ADDRESS);

                    const titleCaseAddresses = addresses.map(address => {
                        const parts = address.split(', ');
                        const formattedParts = parts.map((part, index) => {
                            if (index === parts.length - 1) {
                                // Preserve postcode (DL14 0DX) in uppercase
                                return part.toUpperCase();
                            }
                            return part
                                .split(' ')
                                .map(word => word.charAt(0).toUpperCase() + word.slice(1).toLowerCase())
                                .join(' ');
                        });
                        return formattedParts.join(', ');
                    });

                    req.session.data['addresses'] = titleCaseAddresses;

                    res.redirect('select-subject-uk-address')
                })
                .catch(error => {
                    console.log(error);
                    res.redirect('/discretionary/subject-uk-address')
                });

        }

    } else {
        res.redirect('/find-subject-uk-address')
    }

})
```

### Conclusion

The introduction of the postcode search functionality was a direct response to user feedback and a testament to our commitment to user-centered design. This implementation not only will streamline the address input process but also enhance the overall user experience, making our service meet the users needs.

<a href="/histories" class="govuk-back-link">Back</a>