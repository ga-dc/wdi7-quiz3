# Quiz #3

## Instructions

1. Fork this repo
2. Clone your fork
3. Fill in your answers by writing in the appropriate area, or placing an 'x' in
the square brackets (for multiple-choice questions).
4. Add/Commit/Push your changes to Github.
5. Open a pull request.

**Note**: only place your answer between backticks. Don't modify the backticks,
or the language specifier after them.

## Ruby Basics & Enumerables (meets Beauty and the Beast)


### Question 1

Define a method called `offerRose`, which should take one argument named person.

When called, the method should `puts`, "Would you take this rose and help out
an old beggar, X?", where X is the person passed into the method.

Demonstrate calling the method with an argument of "young prince".

Write your code here:
```ruby
def offerRose(person='Jimmy')
  puts "Would you take this rose and help out an old beggar, #{person}?"
end

def offerRose(person='young prince')
  puts "Would you take this rose and help out a #{person}?"
end
```

### Question 2

Assume the following hash:

```ruby
town = {
  residents: ["Maurice", "Belle", "Gaston"],
  castle: {
    num_rooms: 47,
    residents: "Robby Benson",
    guests: []
  }
}
```

Using Ruby, remove Belle from the town residents, and
add her to the list of guests in the castle.

Write your code here:
```ruby
town = {
  residents: ["Maurice", "Belle", "Gaston"],
  castle: {
    num_rooms: 47,
    residents: "Robby Benson",
    guests: []
  }
}

residents_castle[:key2] = residents.delete(:key1)

```

### Question 3

Assume you have an array of strings representing friend's names:

```ruby
friends = ["Chip Potts", "Cogsworth", "Lumière", "Mrs. Potts"]
```

Using `.each` AND string interpolation, produce output (using `puts`) like so:

```
Belle is friends with Chip Potts
Belle is friends with Cogsworth
Belle is friends with Lumière
Belle is friends with Mrs. Potts
```

Write your code here:
```ruby
words = %w[Chip Potts Cogsworth Lumière Mrs. Potts]
str = " "
words.each { |word| str += "#{word} " }
puts "Belle is friends with" word.each
```

## SQL, Databases, and ActiveRecord (meets Aladdin)

### Question 4

Describe what an ERD is, and why we create them for applications. Also, give an
example of what the attributes and relationships might be for the following
entities (no need to draw an ERD):
<!-- Maybe clarify whether they're meant to give relationships between all four entities or... -->
* Genie
* Lamp
* Person
* Pet

Your answer:
```
An ERD (Entity Relationship Diagram) is a great tool to use when think about different relationship between data in a data base. Relationships can
exist in many forms including: one-to-many, one-to-one, or many-to-one.

The example above(Genie, Lamp; Person, Pet) is a perfect example of  relationships: A genie may come from one lamp; a lamp may belong to many
people; a person may have on or many pets -- usually the pet only has one owner. The owner could only have one pet, which would make that a
one-to-one relationship since pets usually only have one owner.
```

### Question 5

Describe what a schema is, and how we represent a one-to-many relationship in a
SQL database. If you need an example, you can use: people and wishes
(one-to-many).

Your answer:
```
Replace this with your answer
```

### Question 6

**Assume:**
1. Your database two working tables, `genies` and `lamps`.
2. You have a working connection to the database for ActiveRecord.
3. You have active record models defined for `Genie` and `Lamp`, and the
relationships between the two are set up in Active Record.
<!-- Do we want to specifiy what kind of relationship they have, in case some students aren't familiar with the mythology...? -->
4. Lamps have one property, `wishes_remaining`, and genies have one property, `name`.

Write code to do the following:

1. Create a lamp with 3 wishes remaining and a genie named 'Genie'
2. Create a relationship between 'Genie' and the lamp.
3. Update the lamp so it only has one wish left.
  * Oh no... Jafar has Aladdin! Thankfully he's wished to become a genie himself!
4. Create a new Genie named 'Jafar' and put him in a new lamp with 3 wishes left.
5. Free the good Genie by setting his lamp to `nil`


Write your code here:
```ruby
class Lamp {
  @wishes_remaining 3
}
end

class Genie{
  @name 'Genie'
}
end

class Lamp < ActiveRecord::Base
end

class Genie < ActiveRecord::Base
end

class Lamp {
  @wishes_remaining 1
}

class Genie.new {
  @name = Jafar
  @wishes_remaining 3
}
end

class Genie {
  Lamp = nil
}

```

## Sinatra / REST (meets Mulan)

### Question 7

The Chinese Emperor needs an application to help him manage his warriors.
<!-- LOLZ. YES. -->

Describe to him what a RESTful route is, and list what the seven RESTful routes
would look like for such an application.

Your description:
```
RESTful uses different HTTP methods to represent
different actions. In short, Emperor, it gives you more control. If you'd like to move
one or many soldiers at a time,  or find an individual soldier's id, you can do so.
```
Your routes:
```
The ancestors have provided an example of one route; you do the other six!

GET '/warriors/:id'
  * This is the show route, which finds a warrior by ID, and displays information about
  that warrior.

1. '/warriors/'
2. '/warriors/news'
3. '/warriors'
4. '/warriors/:id/edit'
5. 'warriros/:id'
6.  'warriros/:id'

```

### Question 8

Assume:
* Warrior is an ActiveRecord model, with a 'name' attribute.
* You have a Sinatra `app.rb` (or similar file), that defines the following
route:

```ruby
get '/warriors' do
  @warriors = Warrior.all
  erb :"warriors/index"
end
```

Write what an example ERB file (aka view) might look like to list all the warriors:

Write your code here (**NOTE: syntax highlighting doesn't work for ERB in markdown files, so ignore the colors!**):
```html
<h2>Warriors <a href="/warriors/new">(+)</a></h2>

<ul>
  <% @warrior.each do |warriors| %>
    <li>
      <a href="/warrior/<%= warrior.id %>">
        <%= warrior.name %>
      </a>
    </li>
  <% end %>
</ul>
```
