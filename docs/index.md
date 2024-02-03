---
homepage: true
layout: product
includeInBreadcrumbs: true
description:
image:
  src: /assets/opengraph-image.png
  alt: NCTS EU UK map with HMRC logo.
startButton:
  href: "https://docs.google.com/presentation/d/1rrFulF0oOyZoIyhOoHD5h88ViYKr8QJ9JgwkXs8uWtY/edit#slide=id.p3"
  text: Design deck
eleventyComputed:
  title: "{{ pkg.description }}"
  ogImage:
    alt: "{{ options.homeKey }}"
---

<div class="govuk-grid-row">
{% for item in collections["homepage"] %}
  <section class="govuk-grid-column-one-third-from-desktop govuk-!-margin-bottom-8">
    <h2 class="govuk-heading-m govuk-!-font-size-27"><a class="govuk-link govuk-!-font-weight-bold" href="{{ item.url | url }}">{{ item.data.title }} </a></h2>
    <p class="govuk-body">{{ item.data.description | markdown("inline") }}</p>
   
  </section>
{% endfor %}

<section class="govuk-grid-column-full">
    <hr class="govuk-section-break govuk-section-break--visible govuk-section-break--xl govuk-!-margin-top-0">
    <h2 class="govuk-heading-m govuk-!-font-size-27">Prototype</h2>
    <p class="govuk-body">The prototype for this service is currently in version-14</p>
    <p class="govuk-body">Username: prototype
    <p class="govuk-body">Password: thisisabadpassword</p>
    <a href="https://ctc-trader-p5-prototype.herokuapp.com/" class="govuk-link govuk-heading-s" >NCTS5 prototype</a>
  </section>
</div>
