---
layout: post
title: Open-Todo-API
feature-img: "img/sample_feature_img_2.png"
# thumbnail-path: "https://d13yacurqjgara.cloudfront.net/users/3217/screenshots/1686132/webflow_landingpage_1x.jpg"
thumbnail-path: "img/open-todo-api.png"
short-description: basic open to-do list API

---

<a class="button" href="https://github.com/jvg0119/open-todo-api" target="_blank_">
  to github
</a>

<h3>Summary</h3>
<p>Build an extremely usable API for a basic to-to list application. Users will be able to modify their accounts and to-do list items from the command line. This is also a good opportunity to learn how to use the postman software.</p>

<h3>Explanation</h3>
<p>This is a simple but flexible to use app. It allows users to perform basic navigations using curl or postman. </p>

<h3>Problem</h3>
<p>Open To-do API should return JSON representations of uses, lists, and items.</p>
<p>Users should be able to authenticate using their username and password.</p>
<p>Users should be able to create, remove, and update their lists and items.</p>

<h3>Solution</h3>
<p>Install and and setup "Active Model Serializer" gem. Serializer is a very convenient and versatile way of organizing and making an modifications on your JSON output. You can also easily create methods for non-attribute information like for example: full_name or a certain date format.</p>
<p>Incorporate the "authenticate_or_request_with_http_basic" method for user authentication. This is a simple but effective form of authentication.</p>
<p>Add create, destroy, and update action methods for ListsController and ItemsController.</p>

<h3>Result</h3>
<p>Test the API functions using terminal curl and the postman. Everything is working fine.</p>

<h3>Conclusion</h3>
<p>To make the app authentication more robust I replaced the userame/password used by the "authenticate_or_request_with_http_basic" with "authenticate_or_request_with_http_token". </p>

<ul>
  I added role to users (admin and regular) and gave each authorizations:
  <li>Admin can do everything and are only assigned through the console.</li>
  <li>Regular users  can only create, update, show and destroy their own list  and items on their lists.</li>
</ul>

<p>In order to further improve my API testing skills I went ahead and incorporated RSpec with rails_factory_girl testing.
</p>

<p>Checkout the new features: &nbsp;
  <a class="button" href="https://github.com/jvg0119/open-todo-api/tree/7_ec_auth" target="_blank_">
    to github
  </a>
</p>
