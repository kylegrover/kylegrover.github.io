---
layout: page
title: Bio & Contact
myface: kyle-profile.jpg

---
<img class="myface" src="{{ site.cloudinary_url }}/w_250/{{ page.myface }}">

I'm a freelance web developer, programmer, and digital artist in Eugene, Oregon. When I'm not making websites and drinking lots of coffee or tea, I'm probably exploring new digital art mediums, playing indie video games, or checking out some local music.

I'm available for freelance work, check out my [services](/services/).

Sometimes I write words about things, check out my [blog](/blog/).

## Let's Chat

<form name="Contact Page" netlify method="POST" class="contact-form floating-labels">
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
<input style="display: none" name="_next" value="/thanks/">
</form>