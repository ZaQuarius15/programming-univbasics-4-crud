# Basic Arrays: Creating, Retrieving, Updating and Deleting

## Learning Goals

- Create and populate an array
- Add items to an array using different methods
- Remove items from an array using different methods
- Operate on an array using the sort, reverse, and include methods
- Identify elements in an array based on their index number
- Retrieve items from an array
- Reference the Ruby documentation on arrays

## Introduction

This lesson will give a deeper dive on how to create, manipulate, and retrieve
data from arrays.

## Creating an Array

There are a few different ways to make a new array. You can use the literal
constructor or the class constructor.

##### The Literal Constructor

```ruby
my_array = []
```

##### The Class Constructor

```ruby
my_array = Array.new
#  └── []
```

**Advanced:** *Don't worry about the class constructor right now. We'll learn
much more about this later on. We're introducing it briefly here because you may
encounter this syntax if you read through other resources you might find
online.*

To make an array that isn't empty, you can separate each item, known as an
element, by a `,` ("comma") and wrap all the elements inside `[``]` ("square
brackets").

```ruby
puppies = ["bulldog", "terrier", "poodle"]
#  └── ["bulldog", "terrier", "poodle"]

random_numbers = [ 2, 5, 6, 8, 30050]
#  └── [ 2, 5, 6, 8, 30050]

mixed = ["this", "array", 7, 20, "has", 45, "integers", "&", "strings", 309]
#  └── ["this", "array", 7, 20, "has", 45, "integers", "&", "strings", 309]
```

It is possible to create an array that contains disparate data types. In other
words, you could create an array like the one above, that stores both strings
and integers. This is generally discouraged, however. It's best to keep your
arrays populated with only one kind of element.

## Adding Items to an Array

If an array is a storage container for a list of data, then we can imagine
adding and removing individual items. Let's take a look at how we can add
elements to an array.

### Shovel Method

The shovel method employs the "shovel" operator (`<<`) and allows you to add
("shovel") items onto the *end* of an array:

```ruby
famous_cats = ["lil' bub", "grumpy cat", "Maru"]

famous_cats << "nala cat"

puts famous_cats.inspect
# > ["lil' bub", "grumpy cat", "Maru", "nala cat"]

```

**Note:** *The* `.inspect` *method returns a string containing a human-readable
representation of an object. In this case, the list of the strings held in the
array.*

The shovel method (`<<`) is the preferred syntax for adding elements to an
array, however you might see other methods used in examples online:

### The `.push` Method

Calling `.push` on an array with an argument will add that element to the *end*
of the array. It has the same effect as the shovel method explained above:

```ruby
famous_cats = ["lil' bub", "grumpy cat", "Maru"]

famous_cats.push("nala cat")

puts famous_cats.inspect
# > ["lil' bub", "grumpy cat", "Maru", "nala cat"]

```

### The `.unshift` Method

To add an element to the *front* of an array, you can call the `.unshift` method
on it with an argument of the element you wish to add:

```ruby
famous_cats = ["lil' bub", "grumpy cat", "Maru"]

famous_cats.unshift("nala cat")

puts famous_cats.inspect
# > ["nala cat", "lil' bub", "grumpy cat", "Maru"]

```

## Removing Items From an Array

### The `.pop` Method

Calling `.pop` on an array will remove the *last* item from the *end* of the
array. The `.pop` method will also supply the removed element as its return:

```ruby
famous_cats = ["lil' bub", "grumpy cat", "Maru"]
maru_cat = famous_cats.pop

puts famous_cats.inspect
# > ["lil' bub", "grumpy cat"]
puts maru_cat
# > Maru
```

### The `.shift` Method

Calling `.shift` on an array will remove the *first* item from the *front* of
the array. The `.shift` method will also supply the removed element as a return:

```ruby
famous_cats = ["lil' bub", "grumpy cat", "Maru"]
lil_bub = famous_cats.shift

puts famous_cats.inspect
# > ["grumpy cat", "Maru"]
puts lil_bub
# > lil' bub
```

*Note:* If you want to remove items that are not at the beginning or end of an
array, use the [Ruby documentation](http://docs.ruby-lang.org/en/2.0.0/Array.html#method-i-delete_at)
to figure out how.

## Retrieving Items from Array

When you write out a list on a notepad, you typically write each item on its own
line. Whether or not the list is explicitly numbered, the list has a numerology
to it based on the sequence of the lines that the items are listed upon.

Just like the items in our notepad lists, elements in an array are associated
with a number that represents their order. In programming, this number is called
an **index**. While humans typically start their lists at "1", arrays begin
their indexes at `0` (zero). So, the first item in an array will always be "at
index `0`". If we have an array of famous (fictional) cats:

```ruby
famous_cats = ["Cheshire Cat", "Puss in Boots", "Garfield"]
```

The `"Cheshire Cat"` is at index `0` in the array, `"Puss in Boots"` is  a index
`1`, and `"Garfield"` is at index `2`. Indexes will always be *one less* than
the **count**.

To access one of these items in the `famous_cats` array, we can type the name of
the array immediately followed by the relevant index number wrapped in square
brackets (`[]`).

```ruby
famous_cats =  ["Cheshire Cat", "Puss in Boots", "Garfield"]

famous_cats[1]
#  └── "Puss in Boots"

famous_cats[0]
#  └── "Cheshire Cat"

famous_cats[2]
#  └── "Garfield"
```

We can also access array elements by using negative index numbers. The last item
of an array is considered to be stored at an index of `-1`. Let's give it a
shot:

```ruby
famous_cats[-1]
# └── "Garfield"
```

#### Bonus: Using Methods

We can also use the `#first` method on an array to access the first element:

```ruby
famous_cats.first
# └── "Cheshire Cat"
```

We can use the `#last` method to access the last element:

```ruby
famous_cats.last
# └── "Garfield
```

#### A Note on Index Numbers

What happens when we try to access the element stored in an index that doesn't
exist? In other words, let's say we have our `famous_cats` array that contains
three elements. That means that our array contains an element at indexes `0`,
`1`, and `2`. What happens if we try to access an element at index `3`? An index
element that doesn't exist.

Let's take a look:

```ruby
famous_cats[3]
#  └── nil
```

It returns `nil`!

#### Advanced: Finding An Element's Index With `.index()`

To discover the index number of an element within an array, we can use the
`.index()` method. Calling `.index()` on an array with an argument inside the
parentheses will return the *first* index number of an element matching that
argument. If no elements match the argument, then this method will return `nil`.

```ruby
famous_cats = ["Cheshire Cat", "Puss in Boots", "Garfield"]

famous_cats.index("Puss in Boots")
#  └── 1

famous_cats.index("Maru")
#  └── nil
```

This is not an operation you will perform very often. Arrays are used to store
data and usually you will use the index number of an item to access it, not the
other way around.

## Conclusion

## Resources
<iframe width="560" height="315" src="https://www.youtube.com/embed/W0Q_AyfolRw" frameborder="0" allowfullscreen></iframe><p><a href="https://www.youtube.com/watch?v=W0Q_AyfolRw">Intro to Ruby Arrays</a></p>
