### MongoModel
---
https://github.com/spohlenz/mongomodel

```sh
gem install mongomodel
gem install bson_ext
gem 'mongomodel'
rails g mongo_model:config DATABASENAME
railg g model Article title:string body:string published_at:time approved:boolean
rails g model Chapter title:string body:string -E

```


```ruby
class Article < MongoModel::Document
  property :title, String, :default => 'Untitled'
  property :body, String
  property :published_at, Time, :protected => true
  property :approved, Boolean, :default => false, :protected => true
  timestamps!
  validates_preence_of :tilte, :body
  belongs_to :author, :class => User
  scope :published, where(:published_at.ne => nil)
end

```


```yml
development:
  database: mymongodbname
  host: localhost
  port: 27107
  
  
production:
  database: database_name
  replicas:
    - some.host.com:27017
    - another.host.com:27017
  username: username
  password: password
  
```

