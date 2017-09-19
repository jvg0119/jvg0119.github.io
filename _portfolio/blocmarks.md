---
layout: post
title: Blocmarks
feature-img: "img/sample_feature_img_3.png"
#thumbnail-path: "https://d13yacurqjgara.cloudfront.net/users/3217/screenshots/2030966/blocjams_1x.png"
thumbnail-path: "img/blocmarks.png"
short-description: Bookmark urls via email.

---

<a class="button" href="https://github.com/jvg0119/blocmarks" target="_blank_">
  to github
</a>
<a class="button" href="https://blocmarks-joe.herokuapp.com/" target="_blank_">
  to project
</a>

<h3>Summary</h3>
<p>Build an application that allows a user to bookmark URLs via email using mailgun gem, peruse other user's bookmarks and maintain a personal index of categorized bookmarks. </p>

<h3>Explanation</h3>
<p>It's easy to bookmark urls in your browser but eventually it may get cluttered. Blocmark helps manage bookmarks and also to have the ability to share bookmarks with friends.</p>

<h3>Problem</h3>
<p>Users should be able to signup for a free account in order to user the app.</p>
<p>Signed users should be able to: </p>
<ul style="margin-left: 40px;">
  <li>create or edit their own topic.</li>
  <li>add bookmark url on any topic or edit their own bookmark url.</li>
</ul>
<p>Users should also be able email to the app with their url.</p>

<h3>Solution</h3>
<p>Utilized the gems Devise and Pundit for authentication and authorization. Pundit is a nice gem that makes it easy to setup user's access and restrictions in the app.</p>
<p>Use "mailgun" service through heroku to send email to and route it to the blocmark app: </p>
<ul style="margin-left: 40px;">
  <li>send email to app with subject as the topic and the body as the url to be bookmarked.</li>
  <li>if the subject does not match any of the topics in it will create a new topic and add the bookmark there. </li>
  <li>if the email is not found in the database the app will create a new user using this email and give it a default password which they can change later then add the url to the proper topic.</li>
</ul>

<h3>Result</h3>
<p>The app is working properly.</p>

<h3>Conclusion</h3>
<p>Working on this project taught me some valuable lessons. One is how to research and use gems. Gem are nice and convenient. They save you a lot of extra work that you have to do if you do it from scratch. But with that there is an added responsibility to make a thorough and complete research and investigation. And keep in mind your priorities which is to finish the project in a timely manner or whatever other priority you have.    </p>
<p>Also, when working with gems like mailgun or embedly  where you have to use their service and of coarse you'll be using their free or trial version is that they are limited versions. You might run into problems or errors that are caused by these limitations and that could cause you more time in your development. I learned that this is part of the development process. Be aware of it and try to use it to your advantage if you can.</p>


<p>Checkout the new features: &nbsp;
  <a class="button" href="https://github.com/jvg0119/blocmarks/tree/12_readable_urls" target="_blank_">
    to github
  </a>
</p>
