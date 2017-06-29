## Fork examples

https://github.com/noahgibbs/rulers

https://github.com/noahgibbs/best_quotes

## Checkout chapter 5 branch
```
git checkout -b chapter_5_mine chapter_5
```

## Add “multi_json” dependency 
**rulers/rulers.gemspec** 
```ruby
gem.add_runtime_dependency "multi_json"
```
```
bundle install
```

## Create a JSON object
**best_quotes/db/quotes/1.json**
```json
{
  "submitter": "Jeff",
  "quote": "A penny saved is a penny earned.",
  "attribution": "Ben Franklin"
}
```
