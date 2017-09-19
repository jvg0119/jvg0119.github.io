---
layout: post
title: Debugging Tips for New Rails Developer
feature-img: "img/sample_feature_img_3.png"
---

I am not an expert by no means on this subject but in my brief time learning to code I found that a huge part of my time is spent in debugging. It could be very frustrating at times but also very rewarding when once completed or even just by making some progress.
This is a huge topic to cover so I'm going to offer here a few tips that I've come across and help me so far.

### __Learn to use and master the console__   
It's as simple as typing "rails c" or "rails console" on the terminal. You can use "rails c -s" or "rails c --sandbox" don't want to affect the database and have it rollback what you did when you exit the console.
Typically, you'll be working in development environment so that's the default environment.
You can change it to the "test" environment by typing "rails c -e test". Once inside console you can also type "Rails.env" to find out what your environment is in case you forgot.

___Testing your database models:___  
You can type the models name and find it's attributes
```
  User
  Post
```
Access the objects in your models
```
  User.first, or User.find_by(name:"Bill")
```
Find and assign users to a variable like so:  
This will return an array of users created after Jan. 1, 2017 which you can later manipulate.
```
  u =  User.where('created_at > ?', Date.new(2017,1,1))     
```

___Test model associations:___   
This grabs the first user and returns an array of its' posts  
```
  first_user_posts = User.first.posts  (User has_many :posts)
```
this will return this post's user   
```
  user = post.user  (Post belongs_to :user)
```
___Create objects:___  
```
  u = User.new(name: "Mike", email: "mike@email.com")  
  u.save  
  or just use the create method
  u = User.create!(name: "Mike", email: "mike@email.com")
```
There are a lot more things you can do with the rails console or the ruby irb. You can _google or use overstack_ to find out more.
Remember if you have a problem and you want to try something to check or verify it in the console and you don't know or are not sure on how to do it just google it and most of the time you'll get some kind of answer. If you don't get a good answer just try to rephrase your question.

### __Create a small app or a playground app to experiment__
Sometimes your app gets a bit too large to play around with. It has a lot of things going on. If you're trying out something that is complicated or you're altering too many things you may not want to do all this on the app that you're working on. You might even cause some problem while trying out things. Sometimes it's better to just create another app. A real small app with only the things that you need to simulate what you want to do. This makes your experiment or your debugging more manageable and also not risk adding more problems to your app.
You could also create template apps that can be used in the future for this purpose.
I find this very beneficial because with your regular app with lots of things going on you could possible affect other parts of the app or maybe what you're trying will be affected by other sections of the app.
Then you can make notes and comments on this and keep it for future reference or just delete it after.

### __Use the log__
The log is another very powerful tool for troubleshooting. In the beginning it seems like the log was just spitting out a bunch of codes and data that does not mean a lot but as I learned more I found myself looking and reading the logs more. You can get the error message or codes there. And you really need some kind of feedback in order to debug or troubleshoot. The feedback could of coarse be something that the app is not doing or is doing but is incorrect. Feedback could also be in the form of errors or messages that you can get from the log.   
The log is readily available live when you run your app in development. You could also find it in the app under the folder log/development (also available in test and production).  
The errors give you a hint on where to look or what to check. Don't be afraid even the long nasty looking error message. A lot of times you'll find the more meaningful message in the beginning of the error message. You just have to look carefully.

### __Use the byebug gem__
To use byebug all you need to do is add the gem byebug then run bundle install. I believe it is now defaulted in the gemfile for Rails 5.
One of the places I use byebug is to get in the controller. Just add it anywhere in the controller code that you want to check out. For example in the first line in the create method if you're having problems creating a user.
```
def create
  @bookmark = @topic.bookmarks.new(bookmark_params)
  @bookmark.user = current_user
  byebug
    if @bookmark.save
      @bookmark.likes.create!(user: current_user)
  	  flash[:notice] = "Your new bookmark was saved successfully!"
  	  redirect_to topic_path(@topic) #[@topic, @bookmark]
    else
  	 flash[:error] = "There was an error saving your bookmark. Please try again."
  	  render :new
    end
  end
```
Then create a user from the browser. When the code reaches your _byebug_ the app will stop and you'll need to go to the live log terminal (make sure you have this open; you can also put in a marker here or just add some extra spaces). The app will be stopped and it will show the lines in the controller and the word byebug. You now have a console to play with. Here you'll have access to the controller methods within the action create in this case.   
```
(byebug):1: syntax error, unexpected **arg
********** start here *********
                          ^

nil
(byebug) @bookmark
#<Bookmark id: nil, url: "my-test-bookmark.com", topic_id: 3, created_at: nil, updated_at: nil, user_id: 1, slug: nil>
(byebug) current_user
#<User id: 1, name: "Joe", email: "joe@example.com", created_at: "2017-08-28 18:52:14", updated_at: "2017-09-07 00:50:47", role: "regular", slug: "joe">
(byebug)
```
Then type _exit_ to exit byebug or _next_ to go to the next line of code.

You can also use byebug in the views just put it inside the erb symbols <% byebug %>.

Another place I find byebug useful is in my RSpec testing.
```
it "assigns my_post to @post" do
      get :show, params: {topic_id: my_topic.id, id: my_post.id}
      expect(assigns(:post)).to eq(my_post)
      byebug
    end
```

_then run your rspec test:_
```
rspec spec/controllers/posts_controller_spec.rb:30
Run options: include {:locations=>{"./spec/controllers/posts_controller_spec.rb"=>[30]}}

PostsController
  GET #show
Return value is: nil

[29, 38] in /Users/.../bloccit/spec/controllers/posts_controller_spec.rb
   29:     end
   30:     it "assigns my_post to @post" do
   31:       get :show, params: {topic_id: my_topic.id, id: my_post.id}
   32:       expect(assigns(:post)).to eq(my_post)
   33:       byebug
=> 34:     end
   35:     it "renders the #show view" do
   36:       get :show, params: {topic_id: my_topic.id, id: my_post.id}
   37:       expect(response).to render_template(:show)
   38:     end
(byebug) my_topic
#<Topic id: 54, name: "Mkvai destom aqpgznb.", public: true, description: "Qrgmhyb hsj cnv mfsvcrwj exp gpw rfms. Ijsxf lpct ...", created_at: "2017-09-08 20:51:25", updated_at: "2017-09-08 20:51:25">
(byebug)
```

You can checkout the <a href="http://edgeguides.rubyonrails.org/debugging_rails_applications.html#debugging-with-the-byebug-gem" target="_blank_" >Debugging Rails Application (Rails Guide)</a> or the <a href="https://github.com/deivid-rodriguez/byebug" target="_blank_">byebug</a> for more info.

### __Use the pry gem__   
This is another useful gem. I don't use this enough but it adds more options to the regular console. In order to use it just add the gem <a href="https://github.com/rweng/pry-rails" target="_blank_">pry rails</a> to your gemfile then run bundle install.  
Here is a nice tutorial from RailsCast by Ryan Bates <a href="http://railscasts.com/episodes/280-pry-with-rails?autoplay=true"  target="_blank_"> 280 Pry with Rails</a>

### __Miscellaneous tips__  
___User p or puts___
to output to the log.
This is also useful in debugging. Sometimes you may want to see some output or some type of feedback. You can say something like:
```
def index
    @topics = Topic.all.visible_to(current_user)
    puts "**********************"
    p current_user
  end
```
_Then refresh or click to show the topic's index:_
```
Started GET "/topics" for ::1 at 2017-09-08 15:04:59 -0700
Processing by TopicsController#index as HTML
  User Load (0.3ms)  SELECT  "users".* FROM "users" WHERE "users"."id" = $1 LIMIT $2  [["id", 1], ["LIMIT", 1]]
**********************
  CACHE User Load (0.0ms)  SELECT  "users".* FROM "users" WHERE "users"."id" = $1 LIMIT $2  [["id", 1], ["LIMIT", 1]]
#<User id: 1, name: "Joe", email: "joe@example.com", password_digest: "$2a$10$a/5RB6GtE7fbhVNlGR0Jp.j.xsOJgt9D/8cEgVpTaI4...", created_at: "2017-08-05 00:33:54", updated_at: "2017-08-05 00:33:54", role: "admin", auth_token: nil>
  Rendering topics/index.html.erb within layouts/application
```
___Raise an error___
To open a console that you can work in.   
You can do something like this:
```
def create
    @topic = Topic.new(topic_params)
    raise
    if @topic.save
      @topic.labels = Label.update_labels(params[:topic][:labels])
      flash[:notice] = "The topic was saved successfully!"
      redirect_to @topic
    else
      flash[:error] = "Error creating topic. Please try again."
      render :new
    end
  end
```
_Then create a topic:_  
<img src="/img/raise_error.png" alt="raise_error" height="400" >

Raise in an error will create an error and it will also open a console window where you can access in this case the TopicsController. This is very handy.

___Use dev tools like chrome dev tools___  
This is another great tool you can use to find software bugs. This is already built in the browser. You can access Chrome dev tool in three ways:    
 - right click then select inspect
 - _menu_ click on _view_  then select _Developer_ on the dropdown menu then click _develper tool_
 -  for apple _users opt + cmd + i_

 Here is their overview site: <a href="https://developer.chrome.com/devtools" target="_blank_">Chrome DevTools</a>
 You can find a lot of great tips here.

___Use comments to isolate problems___   
Using comments is a great way to isolate parts of your app.
Use the <a href="https://en.wikipedia.org/wiki/Divide_and_conquer_algorithm" target="_blank_">Divide and conquer algorithm</a> to isolate or narrow down your problem. Basically, you're narrowing your search area.

___Use google and stackoverflow___  
When you hit a roadblock or maybe you just need a quick solution to a known problem or maybe you just can't remember the syntax. A quick and easy way to find solution is to google it or use stackoverflow. Google usually defaults to stackoverflow for most coding problems. Most of the time you'll find an answer to your questions or maybe something very close to what you're looking. So, this is a very useful tool to use!

___Don't give up but you also have your priorities and know you limits___  
It does not make sense to keep pounding your head against a brick wall. You'll likely to injure yourself. You need to use your head. Opps! I meant think smart and know when to stop and ask for help.

___Ask for help___    
