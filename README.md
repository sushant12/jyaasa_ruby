# jyaasa_ruby

Simple questions:
  - Difference between symbol and string in rails.
  - Explain how (almost) everything is an object in Ruby
  - What’s your favorite testing tool?
  - What are Gems and which are some of your favorites?
  - What is a class?
  - What is the difference between a class and a module?
  - What is an object?
  - How would you declare and use a constructor in Ruby?
  - How and when would you declare a Global Variable?
  - How would you create getter and setter methods in Ruby?
  - Describe the difference between class and instance variables?
  - Explain some of the looping structures available in Ruby?
  - Explain the difference between a has_one and belongs_to association
  - Explain a polymorphic association



MEDIUM/HARD QUESTIONS:
  - What is a Proc?
  - What is a lambda?
  - What are the three levels of method access control for classes and what do they signify? What do they imply about the method?
  - Explain what functional testing is
  - There are three ways to invoke a method in ruby. Can you give me at least two?
  - Explain this ruby idiom a ||= b
  - What does self mean?
  - What is unit testing (in classical terms)? What is the primary technique when writing a test?
  - | 
    What is the primary difference in these two code snippets?
      // Java
      public boolean isEmpty(String s) {
        return s.length() == 0;
      }
      # ruby
      def empty?(s)
        return s.size == 0
      end 


  - What is your favorite api resource for ruby?
  - What is the difference between Ruby’s Hash and ActiveSupport’s HashWithIndifferentAccess?
  - What is CSRF? How does Rails protect against it?
  - How would you define a Person model so that any Person can be assigned as the parent of another Person (as demonstrated in the Rails console below)? What columns would you need to define in the migration creating the table for Person?
  - |
      What paths (HTTP verb and URL) will be defined by the following snippet in config/routes.rb?
      resources :posts do
        member do
          get 'comments'
        end
        collection do
          post 'bulk_upload'
        end
      end

  - |
      Create a route to be able to display pages with different information about different types of beer. The route should recognize URL paths like /beer/<beer_type> and should use the same controller action for each type of beer with the actually beer type passed into the controller action as a parameter. The valid beer types are as follows
      IPA
      brown_ale
      pilsner
      lager
      lambic
      hefeweizen
      Any other type of beer specified should generate a 404 status code.
  - A Rails-specific question how Date.today differs from Date.current?
  - What is database transactions and how it is represented in Rails.
  - Tell me about your development environment.


Practical Ruby Questions:
  - web scraping . Write a ruby program that gets the headlines for the users displayed from todays edition of ekantipur.com

#Difference between symbol and string in rails.
  
  Symbol is like a string but it is immutable. Normally we use symbols if we are sure that its value will stay unique. Symbol starts with `:` colon . There can be only one instance of any given symbol. Since we don’t use symbols for data processing tasks, they lack most of the classic string manipulation methods.
  
Ruby`s String class is optimized for the data processing side of strings. We want to use strings for data, for things that we might want to truncate, turn to uppercase, or concatenate. They are mutable. A new instance is created everytime we declare a new string. 

#Explain how everything in Ruby is an object

Ruby is OOP language.Everything in ruby comes equipped with their very own methods. 

Ruby will look for the method in the class of the object. If it finds the methods there ruby will call it else it will search for the methods in the super class and try there. It will repeat until it either finds the method or run out of superclasses.

Suppose we have a parent class called `Animal`.

//Animal.rb

`class Animal; end`

and Dog inherits from the Animal class

//Dog.rb

`require_relative 'Animal.rb';
class Dog < Animal; end`

If we were to know what is the superclass of Dog then we would do `puts Dog.superclass` and it would print `'Animal'`.Now if we were to `puts Animal.superclass` it would print `'Object'`

Ruby implicitly sets a superclass `'Object'` unless we specify a superclass ourselves. So 

//Animal.rb

`class Animal; end`

is equivalent to 

//Animal.rb

`class Animal < Object; end`

Since virtually all Ruby objects can trace their ancestry back to Object , virtually all Ruby objects have a set of methods in common:the ones they inherit from Object .

#What is your favourite testing tool?

Testing the codes has proven very effective in SDLC as it tries to eliminate any possible bugs. I tend to use Rspec , a BDD testing framework.

#What are gems and which are some of your favourite?

I do not have a very specific favourite gem but I use rails, pry.

#What is a class?

A class is blue print of an object.

#What is the difference between a class and a module?

Instance variables can only be declared in class. We can create an object by instansiating a class. 

We can created mixin using module by including it inside the class.

#How would you declare and use a constructor in Ruby?

Declaring a constructor
`
  class ClassName
  	def initialize
  	end
  end`
  
  Using a constructor
  
  `class ClassName
  	def initialize
  		puts "Object initiated"
  	end
  end
  ClassName.new  //=> Object initiated `
  
#How and when would you declare a Global Variable?

Using $ infront of a variable name will declare a global variable.

#How would you create getter and setter methods in Ruby?

As the name itself implies, setter sets the vale and getter returns the value. Ruby has provided us with some handy ways to create getters and setters.

 ` attr_reader :name`
 
 will create
 
 ` def name
  	@name
  end`
  
  `attr_writer :name`
  
  will create
  
  `def name=(p)
  	@name = p
  end`
  
  `attr_accessor :name` 
  
  is just a short form of above.
  
#Describe the difference between class and instance variables?

Instance variable is what the class knows. It is also known as state.they’re stored with each object and available to all the instance methods of those objects.no other object can access an object’s instance variables

#What is a Proc?

If the last argument to a method is preceded by an ampersand, Ruby assumes that it is a Proc
object

#What are the three levels of method access control for classes and what do they signify? What do they imply about the method?

private - can only be called from inside the class that defined them and its subclasses, 


  protected - Any instance of a class can call a protected method on any other instance of the class, 
  
  
  public - available to everyone except for initialize , which is always private
  
  
  The Ruby philosophy is that the programmer is in charge. If you want to declare some method private, fine. Later, if someone, perhaps you, wants to violate that privacy, fine again. You are in charge and presumably you know what you are doing.
  
#Explain this ruby idiom a ||= b

Assign a value to a variable only if that variable isn’t already set.This is almost, but not quite, the same as `var = var || "default value"` . It differs in that no assignment is made at all if the variable is already set.

#What is the primary difference in these two code snippets?
      // Java
      public boolean isEmpty(String s) {
        return s.length() == 0;
      }
      # ruby
      def empty?(s)
        return s.size == 0
      end 
      
In short, the primary difference in them is duck-typing.If we continue to write static type style base classes, our code will continue to be much bulkier than it might be.

#What is your favorite api resource for ruby?

The documentation in itself is a treasure however I keep aside "programming ruby: the pragmatic programmers guide" and lots of other books. I like to read a lot.

#Tell me about your development environment.
   OS: Linux Mint 17.1 Rebecca
   VC: git
   TextEditor: Sublime
   RVM
   REPL console: pry
   gem v: 2.4.8
   ruby v: 2.2.3
   rails v: 4.2.4
