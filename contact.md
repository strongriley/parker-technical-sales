---
layout: page
permalink: /contact/
title: Contact Us
redirect_from:
  - contact.html
  - quote.php
---

<div class="desktop-2-up">
  <div>
    <a href="https://www.google.com/maps/place/2424+Armstrong+St,+Livermore,+CA+94551/@37.6995834,-121.8123017,17z/data=!3m1!4b1!4m2!3m1!1s0x808fe89d3f02cfc9:0x71d211b67f0afb54" target="_blank">
    2424 Armstrong Street<br>
    Livermore, CA 94551<br>
    </a>
    Phone: (925) 362-9450<br>
    Fax: (925) 955-9520<br>
    <a href="mailto:sales@parkertechnicalsales.com">
      sales@parkertechnicalsales.com
    </a>
  </div>
  <div>
    <img alt="office" class="office" src="{{ site.url }}/images/office.jpg">
  </div>
</div>

<p>
  <a name="form"></a>
  <h2 class="clearfix">Request a Quote</h2>
  <form class="contact" action="//formspree.io/eponymous@rileystrong.com" method="POST">
      <label for="name">Full name</label>
      <input id="name" type="text" name="name" placeholder="Your name">

      <label for="company">Company name</label>
      <input id="company" type="text" name="company" placeholder="Your company">

      <label for="phone">Phone number</label>
      <input id="phone" type="tel" name="phone-number" placeholder="(925) 555-4455">

      <label for="email">Email address</label>
      <input id="email" type="email" name="_replyto" placeholder="email@example.com">

      <label for="help">How may we help you?</label>
      <textarea id="help" name="help" rows="5"></textarea>

      <input type="text" name="_next-TODO" style="display:none" />
      <input type="text" name="_subject" value="New contact request" style="display:none" />
      <input type="text" name="_gotcha" style="display:none" />

      <input class="btn" type="submit" value="Send">
  </form>
</p>
