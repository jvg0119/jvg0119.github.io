---
layout: post
title: Blocipedia
feature-img: "img/sample_feature_img.png"
# thumbnail-path: "https://d13yacurqjgara.cloudfront.net/users/3217/screenshots/2030966/blocjams_1x.png"
thumbnail-path: "img/blocipedia.png"
short-description: To create/collaborate wikis.

---

<a class="button" href="https://github.com/jvg0119/blocipedia3" target="_blank_">
  to github
</a>
<a class="button" href="https://blocipedia3-joe.herokuapp.com/index" target="_blank_">
  to project
</a>

<h3>Summary</h3>
<p>Build a markdown-based wikis application that allows users sign-up then upgrade to a premium account. With a premium account they have the ability to create private wikis where they can have collaborators on their wikis.</p>

<h3>Explanation</h3>
<p>Wikis are a great way to share hobbies or other community-sourced contents. Users can also collaborate with work-related projects using private wikis.</p>

<h3>Problem</h3>
<p>Guest users should be able to browse through the public wikis</p>

<p>Signed in users are able to create and destroy their own wikis or update other public wikis. And then upgrade to premium account for a small fee.</p>

<p>Premium account users  have additional privileges of being able to create and allow collaborators to their private wikis.  

<p>Admin users can also be assigned that will have access to everything.</p>

<p><em>Other options to improve app:</em></p>
<ul style="margin-left: 40px;">
  <li>generate Blocipedia's views using HAML instead of ERB</li>
  <li>make wiki urls readable</li>
  <li>provide preview of the markdown as it is being edited</li>
</ul>

<h3>Solution</h3>
<p>Use the gem "devise" for authentication. This is a proven authentication solution. It is scalable and flexible. It can also be customize if needed.</p>
<p>Use "sendgrid" to send email confimation and "figaro"to store our credentials.</p>
<p>User the gem "pundit" for authorization. This is also another proven solution for authorization that is also highly customizable.</p>
<p>Use the "stripe" gem to charge for premium upgrade account. Stripe is a great way to accept payments online and in mobile apps. They handle billions of dollars every year for different types of businesses around the world.</p>
<p>Use "redcarpet" gem for markdown. This gem allows us to implement markdown in a very simple way.</p>
<p>Add collaborator resource to implement wiki collaborations among premium users. Utilize the has_many :through association for users and wikis.</p>
<ul style="margin-left: 40px;">
  <li>wiki has_many :wiki_collaborations, through: :collaborators, source: :wiki</li>
  <li>user has_many :wiki_collaborators, through: :collaborators, source: :user</li>
</ul>
<p>Admin users will be assigned manually through the console.</p>
<p>Role is implemented using ActiveRecord Enums which is a nice and easy way to create the role attributes.</p>

<p>Convert the ERB view files to HAML; this make the view codes much cleaner and easier to read.</p>
<p>Incorporate "friendly_id" gem. This makes adding a slug and making the urls more readable much easier to implement.</p>
<p>Add "EpicEditor" an embeddable JavaScript Markdown Editor. This was not a straight forward implementation. When I finally had it working as a preview it didn't seem like it was compatible with "redcarpet" markdown solution. When I updated it the markdown result was incorrect. This app detail needs more research and experimentation and of coarse more time to develop. EpicEditor may not be the best preview solution for this app. Did not further pursue this app enhancement.</p>

<h3>Result</h3>
<p>Overall the Blocipedia app is working nicely. One feature that I added but doesn't seem to work as good is the wiki tab selection and pagination. This feature allows to show only the public or private or all the wikis. Every time you select a different page it always defaults to the "All Wikis" tab then you have to hit the "public" or "private" tab which ever you're trying to get. I would say this area needs more research.</p>

<h3>Conclusion</h3>
<p>All the proven gems like devise and pundit with millions of downloads worked very well. I also tried the EpicEditor gem but could not get it to work well. Upon checking its download times, it had a measly download of just around 3900.    it had a very low download time of just around 3900. It also had a JavaScript implementation but its instructions were not clear. And once I got it to work it did not work quite well with the redcarpet gem as I mentioned earlier.</p>
<p>I learned a lot about the development process going through this app mostly on my own. One thing I learned is that the preparation, research and exploration part of the development is very critical. In order for the coding part to run smoothly you have to do a great deal amount of preparation work. The open source market is very fluid. You really need to do your due diligence to ensure you're putting the right gems and features together correctly.</p>

<p>Checkout the new features: &nbsp;
  <a class="button" href="https://github.com/jvg0119/blocipedia3/tree/8_ec" target="_blank_">
    to github
  </a>
</p>
