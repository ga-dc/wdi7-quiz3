## Ruby Basics & Enumerables (meets Beauty and the Beast)


### Question 1

Define a method called `offerRose`, which should take one argument named person.

When called, the method should `puts`, "Would you take this rose and help out
an old beggar, X?", where X is the person passed into the method.

Demonstrate calling the method with an argument of "young prince".

Write your code here:
```
def offerRose (person)
  puts "Would you take this rose and help out an old beggar, " + person + "?"
end

offerRose('young_prince')
```
### Question 2

Assume the following hash:

```
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
```
town[:castle][:guests] << town[:residents].delete("Belle")

# ```
# town[:residents].delete( "Belle" )
# +town[:castle][:guests] = "Belle"
# other possible solution? or is this is just deleting and creating a new value in the array?

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

friends.each do |f|
  puts "Belle is friends with " + f
end

```

## SQL, Databases, and ActiveRecord (meets Aladdin)

### Question 4

Describe what an ERD is, and why we create them for applications. Also give an
example what the attributes and relationships might be for the following
entities (no need to draw an ERD):
<!-- Maybe clarify whether they're meant to give relationships between all four entities or... --> # I'm having a hard time understanding what you mean by this...

* Genie
* Lamp
* Person
* Pet

Your answer:
```
 An entity-relationship (ER) diagram is a specialized graphic that illustrates the relationships between entities in a database. ER diagrams often use symbols to represent three different types of information. Boxes are commonly used to represent entities. Diamonds are normally used to represent relationships and ovals are used to represent attributes.

 A person can have many Lamps and each lamp one Genie?
 and a person can have one pet?... I'm unsure about how to explain this.
```

### Question 5

Describe what a schema is, and how we represent a one-to-many relationship in a
SQL database. If you need an example, you can use: people and wishes
(one-to-many).

Your answer:
```
A schema is a collection of database objects (as far as this hour is concerned—tables) associated with one particular database username. This username is called the schema owner, or the owner of the related group of objects. You may have one or multiple schemas in a database.

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
# code here
Lamp.create(wishes_remaining: 3)

Genie.create(name: "Genie")

class Genie < ActiveRecord::Base
  has_one :lamp
end

class Lamp < ActiveRecord::Base
  belongs_to :genie
end

no_one_lamp = Lamp.create(id: 1, wishes_left: 3, genie_id: 1)

no_one_lamp.update(wishes_left: 1)

Jafar_genie = Genie.create(id: 2, name: "Jafar")

Jafar_lamp = Lamp.create(id: 2, wishes_left: 3, genie_id: 2)

Jafar_lamp.update(genie_id: nil)

## Sinatra / REST (meets Mulan)

### Question 7

The Chinese Emperor needs an application to help him manage his warriors.

Describe to him what a RESTful route is, and list what the seven RESTful routes
would look like for such an application.

Your description:
```RESTful routes take advantage of the built-in REST orientation of Rails to wrap up a lot of routing information in a single declaration
```
Your routes:
```
The ancestors have provided an example of one route; you do the other six!

GET '/warriors/:id'
  * This is the show route, which finds a warrior by ID, and displays information about that warrior.

GET '/warriors'
```
*Gets all of the info from warriors

POST '/warriors'
Creates a new warriors

PUT '/warrior/:id'
*Updates the info about a warriors

PATCH '/warrior/:id'
*Updates some of the info for a warriors

DELETE '/warriors/:id'
*Deletes a warrior from the app
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

<%= @warriors.each do |w| %>
<ul>
<li><%%= warrior.name%></li>
</ul>
<% end %>
```