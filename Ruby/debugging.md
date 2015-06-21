# Debugging

* [Prying open the black box](https://www.youtube.com/watch?v=IjbYhE9mWuk)
* [blame_parent](https://github.com/chancancode/blame_parent)
* [RailsConf 2015 - Speed Science](https://www.youtube.com/watch?v=m2nj5sUE3hg)

```
pp instance_values
<%= console %>
bundle open activerecord
gem pristine activerecord

byebug
method(:compute_type).source_location
method(:compute_type).source
method(:compute_type).owner
method(:compute_type).comment

gem 'method_source'

git log <filename>
git blame <filename>
git show <SHA>
git blame <SHA>^ <filename>
```

