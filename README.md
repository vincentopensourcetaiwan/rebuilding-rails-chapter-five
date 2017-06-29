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

## Add file_model object
**rulers/lib/rulers.rb**
```ruby
require "rulers/file_model"
```
**rulers/lib/rulers/file_model.rb**
```ruby
require "multi_json"
module Rulers
  module Model
    class FileModel
      def initialize(filename)
        @filename = filename
        # If filename is "dir/37.json", @id is 37
        basename = File.split(filename)[-1]
        @id = File.basename(basename, ".json").to_i
        obj = File.read(filename)
        @hash = MultiJson.load(obj)
      end

      def [](name)
        @hash[name.to_s]
      end

      def []=(name, value)
        @hash[name.to_s] = value
      end

      def self.find(id)
        begin
          FileModel.new("db/quotes/#{id}.json")
        rescue
          return nil
        end
      end
    end
  end
end
```