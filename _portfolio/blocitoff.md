---
layout: post
title: Blocitoff
feature-img: "img/sample_feature_img_2.png"
# thumbnail-path: "https://d13yacurqjgara.cloudfront.net/users/3217/screenshots/2030974/bloctalk_1x.png"
thumbnail-path: "img/blocitoff.png"
short-description: Self-destructing to-dos.

---

<a class="button" href="https://github.com/jvg0119/blocitoff" target="_blank_">
  to github
</a>
<a class="button" href="https://joe-blocitoff.herokuapp.com/" target="_blank_">
  to project
</a>

<h3>Summary</h3>
<p>Build an application that allows users to create to-do lists and have it self-destruct after seven days. This will need a good authentication system to make sure each user only access their own profile. It will also need a task that will be setup to automatically run each day and delete to-dos more than seven days.</p>

<h3>Explanation</h3>
<p>To-do lists are notorious for collecting junk: to-do items that aren't very important but you just want to remember. Blocitoff will keep your list manageable by automatically deleting them if they're not completed after seven days.</p>

<h3>Problem</h3>
<p>User profile should only be accessible to each user signed in and is clean and easy to manage.</p>
<p>It should also have a self-destructing to-do item list.</p>

<h3>Solution</h3>
<p>Use Devise for authentication which is a proven and flexible system with verifiable email confirmation.</p>
<p>Create a user show profile page that displays his list to-do items and a to-do creation form.</p>
<p>User ajax to delete to-dos when manually completing them.</p>
<p>Create task to delete all to-dos older than seven days. This can be triggered manually or automatically.</p>

<h3>Result</h3>
<p>The app worked very well. It's simple and easy to use. I can add to-do items and when manually completed an item it is deleted from the list.</p>

<h3>Conclusion</h3>
<p>In conclusion I added a few enhancement to this app.</p>
<p>I recreated the app using authentication from scratch with bcrypt gem.</p>
<p>I also used TDD to build it. I tested the controllers, models, and features. I used RSpec and Capybara with FactoryGirl.</p>
<p>I also automated my rake task using the Whenever gem. Tested this feature by setting up smaller time frames for my automatic deletion. Instead of seven days I used a few minutes only to be able to do several tests.</p>

<p>Checkout the new features: &nbsp;
  <a class="button" href="https://github.com/jvg0119/blocitoff_ec" target="_blank_">
    to github
  </a>
</p>
