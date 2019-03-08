---
layout: page
title: Bio & Contact
permalink: "/contact/"
myface: "/uploads/kyle-profile.jpg"

---
<img class="myface" src="{{ page.myface | relative_url }}">

I'm a freelance web developer, programmer, and digital artist living in beautiful Santa Cruz, California.
When I'm not making websites and drinking lots of coffee, I'm probably getting lost in video games, working on art, or checking out some live music.

I'm available for freelance work, check out my [services](/services/).

## Let's Chat

<form action="https://formspree.io/kyle@kylegrover.com" method="POST" class="contact-form floating-labels">
   <div class="form-field-row">
      <div class="form-field">
         <input id="name" class="input-text" type="text" required>
         <label for="name">Name</label>
      </div>
      <div class="form-field">
         <input id="_replyto" class="input-text" type="email" required>
         <label for="email">E-mail</label>
      </div>
   </div>
   <div class="form-field">
      <input id="message" class="input-text" type="text" required>
      <label for="message">Message</label>
   </div>
   <div class="form-field align-center">
      <input class="submit-btn" type="submit" value="Submit">
   </div>
    <input style="display: none" name="_gotcha">
    <input style="display: none" name="_next" value="/thanks">
</form>