# Quiz: Advanced Class Methods

???

## Advanced Class Methods

?: `.all` exposes the `@@all` class variable and its data to the rest of the application.

(X) True ( ) False

?: `self.all` is a class method for reading the data stored in the class variable `@@all`.

(X) True ( ) False

?: To avoid writing repetitious code every time you want to search an object, what can be done?

( ) Return the full list of objects using `.all` ( ) Write a SQL query ( ) Use the Ruby method `.find` (X) Encapsulate the search logic into a class method

?: Within `#initialize`, an instance method, `self` will refer to an to the entire class.

( ) True (X) False

?: If we built a `Person` class that can parse a CSV in a method called `.new_from_csv`, what would this be called?

(X) Custom class constructor ( ) Low-level abstraction ( ) Class instance method ( ) Class finder

?: In a `Car` class, in order to access `Car.all` in `#initialize`, you would need to use `self.class.all`, and then invoke the `Car.all` method.

(X) True ( ) False

?: What benefits can class methods provide?

( ) Improved maintainability of the codebase ( ) a more readable API for the rest of our application ( ) Encapsulated logic (X) All of the above

?:

```ruby
class Person
  attr_accessor :name
  @@all = []
  def self.all
    @@all
  end

  def initialize(name)
    @name = name
    @@all << self
  end

  def normalize_name
    self.name.split(" ").collect{|w| w.capitalize}.join(" ")
  end

  def self.normalize_names
    self.all.each do |person|
      person.name = person.normalize_name
    end
  end
end
```

What action does the `self.normalize_names` method perform?

( ) It converts each name in the Person class to an uppercase version ( ) It converts the name of an instance of Person to an uppercase version ( ) It converts the name of an instance of Person to a capitalized version (X) It converts each name in the Person class to a capitalized version

?:

```ruby
class Car
  attr_accessor :make
  @@all = []
  def self.all
    @@all
  end

  def initialize(make)
    @make = make
    @@all << self
  end

  def self.destroy_all
    self.all.clear
  end
end
```

What does the `Car.destroy_all` method do in this class?

( ) It drops the database table (X) It uses the `Array#clear` method to empty the `@@all` array ( ) It deletes an instance of the `Car` class ( ) It empties the database table

?: A key to writing maintainable code is designing functionality that is closed to modification but open to extension.

(X) True ( ) False

???
