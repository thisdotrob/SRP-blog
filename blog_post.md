What is the Single Responsibility Principle?
============================================
Basically, this: <br><br>
![SRP image](./srp.jpg)
<br><br>

As clever as it might look, it won't work well in practice and will be hard
to use if it is overcomplicated.

In OOP, adhering to the principle means that every class should have
responsibility for only a single part of the software's functionality.

The following code does not adhere to the SRP, as it is responsible for landing
the plane (i.e. setting `@flying` to false) and also for deciding if the weather
is stormy:
```ruby
def land
  raise 'Too stormy to land.' if rand > 0.9
  @flying = false
end
```
To adhere to the SRP you could refactor as follows:
```ruby
def land
  raise 'Too stormy to land.' if Weather.stormy?
  @flying = false
end

class Weather
  def self.stormy?
    rand > 0.9
  end
end
```

SRP keeps code simple, easy to understand and easy to maintain.
