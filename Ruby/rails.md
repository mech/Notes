# Rails

* [Favorite Ruby gems and services](https://medium.com/@riklomas/89fb47341c05)
* [Infinite scrolling in Rails](http://www.sitepoint.com/infinite-scrolling-rails-practice/)
* [Reading Rails series!](http://monkeyandcrow.com/blog/reading_rails_how_does_message_verifier_work/)
* [Some nice gems here](http://www.22ideastreet.com/blog/2014/04/30/starting-on-an-existing-rails-project/)
* [Rails idioms considered harmful](http://jgaskins.org/blog/2014/5/18/rails-idioms-considered-harmful)
* [ActiveSupport::Notifications, statistics and using facts to improve your site](http://www.reinteractive.net/posts/141-activesupport-notifications-statistics-and-using-facts-to-improve-your-site)
* [Geo pinpoint IP](http://voiceofchunk.com/2014/07/12/getting-geolocal-with-pointpin/)
* [Nice blog on Rails](http://dev.mensfeld.pl/)
* [Nice blog on Rails - ninefold](https://ninefold.com/blog/)
* [GoRails - Video lessons](https://gorails.com/)
* [S3 and Rails](http://blog.littleblimp.com/post/53942611764/direct-uploads-to-s3-with-rails-paperclip-and)
* [SSL with Rails](http://collectiveidea.com/blog/archives/2010/11/29/ssl-with-rails/)
* [Inside ActionDispatch and Rack](http://pothibo.com/2013/11/ruby-on-rails-inside-actiondispatch-and-rack/)
* [Thin and SSL](http://makandracards.com/makandra/15903-using-thin-for-development-with-ssl)

## Association Proxy
* [Advanced Proxy Usage](http://pivotallabs.com/advanced-proxy-usage-part-i/)
* [AP and caching](http://www.elevatedcode.com/2007/03/16/rails-association-proxies-and-caching.html)



## Object-Oriented Rails

* [Rails - The Missing Parts - Interactors](http://eng.joingrouper.com/blog/2014/03/03/rails-the-missing-parts-interactors)
* [Don't just dump code into your models](http://blog.sensible.io/2014/04/19/don-t-just-dump-code-into-your-models.html)
* [Service Objects](http://brewhouse.io/blog/2014/04/30/gourmet-service-objects.html)
* [Bus](https://github.com/minio-sk/bus)
* [The right way to code DCI in Ruby](http://mikepackdev.com/blog_posts/24-the-right-way-to-code-dci-in-ruby)

## Build

* [Goodbye, Sprockets! A Grunt-based Rails asset pipeline](http://blog.pedago.com/2014/01/21/goodbye-sprockets-a-grunt-based-rails-asset-pipeline/)

## 4.0

Rails 4 is thread-safe by default (good for `thin` and `puma`). You need to ensure your application (and its dependencies) are thread-safe, which means avoiding global state. See [here](http://tenderlovemaking.com/2012/06/18/removing-config-threadsafe.html)

* [Digging into Rails 4](http://code.tutsplus.com/tutorials/digging-into-rails-4--net-31255)
* [What's new in ActiveRecord](http://blog.remarkablelabs.com/2012/12/what-s-new-in-active-record-rails-4-countdown-to-2013)
* [Upgrading from Rails 3.2 to Rails 4.0](http://dev.mensfeld.pl/2013/07/upgrading-to-rails-4-0-from-rails-3-2-test-case-part-ii-assets-models/#initialize)

## 4.1

* [ActiveRecord enum vs PostgreSQL's enum](http://www.postgresql.org/docs/9.2/static/datatype-enum.html)
* [Favourite things about Rails 4.1](http://www.reinteractive.net/posts/177-my-favourite-things-about-rails-4-1)

## 4.2

* [From Rails 3.2 to Rails 4.2](http://technology.customink.com/blog/2014/09/16/from-rails-3.2-to-4.2/?utm_source=rubyweekly&utm_medium=email)

## ActiveRecord

* [7 patterns to refactor fat ActiveRecord models](http://blog.codeclimate.com/blog/2012/10/17/7-ways-to-decompose-fat-activerecord-models/)

## Arel

```
User.find_or_initialize_by_email('mech@me.com')  # Rails 3.2
User.find_or_initialize_by(email: 'mech@me.com') # Rails 4.0
```

## Caching

* [Advanced caching in Rails](http://hawkins.io/2012/07/advanced_caching_revised/)

## Controller

* [Callbacks on success and failure like Jim Weirich](http://janjiss.github.io/blog/2014/05/14/callbacks-and-ruby/)


## Notable Gems

See [Monterail's list of useful gems](https://github.com/monterail/guidelines/blob/master/gems.md)

* [Lograge - Taming Rails' default request logging](https://github.com/roidrage/lograge)
* [Figaro - For configuring Rails application like ENV settings](https://github.com/laserlemon/figaro)

## Security

* [OWASP's cheatsheet](https://www.owasp.org/index.php/Ruby_on_Rails_Cheatsheet)

## Tips

```
def initialize(attributes={})
  @user = User.new(attributes.slice(:name, :email))
end
```