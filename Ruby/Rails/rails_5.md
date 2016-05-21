# Rails 5

https://www.railsspeed.com/

* [**Container-Ready Rails 5**](https://blog.heroku.com/archives/2016/5/2/container_ready_rails_5)
* [BigBinary Rails 5 features](http://blog.bigbinary.com/categories/Rails%205)
* [`protect_from_forgery`](https://github.com/rails/rails/issues/18329)
* [The end of `alias_method_chain`](http://www.justinweiss.com/articles/rails-5-module-number-prepend-and-the-end-of-alias-method-chain/)
* [What's new in Rails 5](http://www.rubyexperiments.com/rails-5-release-date-whats-new-resources/)
* [Rails 5: What's new](https://medium.com/evil-martians/the-rails-5-post-9c76dbac8fc#.378zs9gi8)
* [Ruby Web Dev The Other Way](http://rwdtow.stdout.in/)

## Action Cable

* [ActionCable, Redux and React](https://articles.startuprocket.com/rails5-actioncable-redux-and-react-walking-through-an-example-chat-application-84fced7c5d27#.cfg9858ud)
* [Action Cable - Friend or Foe?](https://www.nateberkopec.com/2015/09/30/action-cable.html)

## Rails 5 API

* [Improvements to error responses in Rails 5 API mode](https://wyeworks.com/blog/2016/1/12/improvements-to-error-responses-in-rails-5-api-mode)

## Middlewares

* `ActionDispatch::ParamsParser` is replaced by `ActionDispatch::Request`. See https://github.com/rails/rails/commit/38d2bf5fd1f3e014f2397898d371c339baa627b1

## Collection Cache

* [Rails 5 - Much Faster Collection Rendering](https://dev.firmafon.dk/blog/rails-5-much-faster-collection-rendering/)

```ruby
cache(@users) do
end
```