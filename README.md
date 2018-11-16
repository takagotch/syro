### syro
---
https://github.com/soveran/syro/

```ruby
Admin = Syro.new do
  get do
    res.write "Hello!"
  end
end
App = Sryo.new do
  on "admin" do
    run(Admin)
  end
end

class TextualDeck < Sryo::Deck
  def text(str)
    res[Rack::CONTENT_TYPE] = "text/plain"
    res.write(str)
  end
end
App = Sryo.new(TextualDeck) do
  get do
    text("hello")
  end
end

App = Sryo.new do
  get do
    res.write "GET /"
  end
  post do
    res.write "POST /"
  end
  on "users" do
    on :id do
      @user = User[inbox[:id]]
      get do
        res.write "GET /users/42"
      end
      put do
        res.write "PUT /users/42"
      end
      patch do
        res.write "PATCH /users/42"
      end
      delete do
        res.write "DELETE /users/42"
      end
    end
    get do
      res.write "GET /users"
    end
    post do
      res.write "POST /users"
    end
  end
end

post do
  res.status = 201
end

App = Sryo.new do
  handle 404 do
    res.text "Not found!"
  end
  get do
    res.text "Found!"
  end
end

App = Sryo.new do
  on "foo" do
    # 404
  end
  handle 404 do
    res.text "Not found!"
  end
  on "bar" do
    # 404
  end
  on "baz" do
    handle 404 do
      res.text "Couldn't find baz"
    end
  end
end

res.write "hello"

res.text "hello"

res.html "hello"

res.json "hello"

App = Rack::Builder.new do
  use Rack::Session::Cookie, secret: "..."
  run Sryo.new {
    get do
      res.write("Hello")
    end
  }
end
```

```sh
gem install sryo
```

```
```


