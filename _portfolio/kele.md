---
layout: post
title: Kele
feature-img: "img/sample_feature_img.png"
# thumbnail-path: "https://d13yacurqjgara.cloudfront.net/users/3217/screenshots/1686132/webflow_landingpage_1x.jpg"
thumbnail-path: "img/kele.png"
short-description: Kele gem API client

---

<a class="button" href="https://github.com/jvg0119/kele" target="_blank_">
  to github
</a>

<h3>Summary</h3>
<p>Build a Ruby Gem API client (Kele) to access the Bloc API.</p>

<h3>Explanation</h3>
<p>You can access Bloc API endpoints using the terminal with curl. Kele is an API Client to provide an easy access to and use these endpoints. </p>

<h3>Problem</h3>
<p>Users should be able to initialize and authorize Kele with a Bloc username and password.</p>
<p>Users should be able to retrieve current user as a JSON blob, mentor's availability, roadmaps and checkpoints.</p>
<p>Users should be able to retrieve a list of messages and respond to existing message and create a new thread.</p>
<p>Users should also be able to submit checkpoint assignments.</p>

<h3>Solution</h3>
<p>Create the Kele Gem. The minimum and/or main content of the gem are kele.gemspec and lib/kele.rb. Then added "HTTParty" gem which provided a programatic Ruby interface to make HTTP requests.</p>
<p>Create methods (initialize, get_me, get_mentor_availability, get_roadmap and get_checkpoint, get_messages, create_messages, and create_submissions) to access the Bloc API. Test the methods using IRB and also by using the postman software.</p>
<p></p>
<p></p>

<h3>Result</h3>
<p>Tested all the methods in IRB all are working.</p>

<h3>Conclusion</h3>
<p>This is a new experience for me. It's a bit abstract in the beginning because we haven't created a gem prior to this. It was a good learning experience creating and testing the gem.</p>
