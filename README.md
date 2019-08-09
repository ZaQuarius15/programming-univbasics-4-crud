# Array Basics: Creating, Retrieving, Updating and Deleting

## Learning Goals

- Create an `Array`
- Add items to an `Array`
- Remove items from an `Array`
- Retrieve items from an `Array`
- Identify elements in an `Array` based on their index number

## Introduction

Conceptually, we know what `Array`s are and what they look like. Now we can learn
details like how to create, manipulate, and retrieve data from `Array`s.

## Create an Array

There are a few different ways to make a new `Array`. You can use the _literal_
constructor or the _class_ constructor.

### The Literal Constructor

```ruby
my_array = []
#=> []
```

### The Class Constructor

```ruby
my_array = Array.new
#=> []
```

**Advanced:** *Don't worry about the class constructor right now. We'll learn
much more about this later on. We're introducing it briefly here because you
may encounter this syntax in other resources.*

To make an `Array` that isn't empty, you can separate each item, known as an
_element_, by a `,` ("comma") and wrap all the elements inside `[``]` ("square
brackets").

```ruby
puppies = ["bulldog", "terrier", "poodle"]
#=> ["bulldog", "terrier", "poodle"]

random_numbers = [ 2, 5, 6, 8, 30050]
#=> [ 2, 5, 6, 8, 30050]

mixed = ["this", "array", 7, 20, "has", 45, "integers", "&", "strings", 309]
#=> ["this", "array", 7, 20, "has", 45, "integers", "&", "strings", 309]
```

It is possible to create an `Array` that contains different data types. In
other words, you could create an `Array` like the one above that stores both
`String`s and `Integer`s. However, this is generally discouraged. It's best to
keep your `Array`s populated with only one kind of element.

## Add Items to an Array

If an `Array` is a storage container for a list of data, then we can imagine
adding and removing individual items. Let's take a look at how we can add
elements to an `Array`.

### The Shovel Method

The **shovel** method employs the "shovel" operator (`<<`) and allows you to
add (or "shovel") items onto the *end* of an `Array`:

```ruby
famous_cats = ["lil' bub", "grumpy cat", "Maru"]

famous_cats << "nala cat"

p famous_cats
#=> ["lil' bub", "grumpy cat", "Maru", "nala cat"]

```

The shovel method (`<<`) is the preferred syntax for adding elements to an
`Array`, however you might see other methods used in examples online.

### The `.push` Method

Calling `.push` on an `Array` with an argument will add that element to the *end*
of the `Array`. It has the same effect as the shovel method explained above:

```ruby
famous_cats = ["lil' bub", "grumpy cat", "Maru"]

famous_cats.push("nala cat")

p famous_cats
#=> ["lil' bub", "grumpy cat", "Maru", "nala cat"]

```

### The `.unshift` Method

To add an element to the *front* of an `Array`, you can call the `.unshift` method
on it with an argument of the element you wish to add:

```ruby
famous_cats = ["lil' bub", "grumpy cat", "Maru"]

famous_cats.unshift("nala cat")

p famous_cats
#=> ["nala cat", "lil' bub", "grumpy cat", "Maru"]

```

## Remove Items from an Array

### The `.pop` Method

Calling `.pop` on an `Array` will remove the *last* item from the *end* of the
`Array`. The `.pop` method will also supply the removed element as its return:

```ruby
famous_cats = ["lil' bub", "grumpy cat", "Maru"]
maru_cat = famous_cats.pop

p famous_cats
#=> ["lil' bub", "grumpy cat"]
p maru_cat
#=> Maru
```

### The `.shift` Method

Calling `.shift` on an `Array` will remove the *first* item from the *front* of
the `Array`. The `.shift` method will also supply the removed element as a return:

```ruby
famous_cats = ["lil' bub", "grumpy cat", "Maru"]
lil_bub = famous_cats.shift

p famous_cats
#=> ["grumpy cat", "Maru"]
p lil_bub
#=> lil' bub
```

**Note:** If you want to remove items that are not at the beginning or end of
an `Array`, use the [Ruby documentation][rb-array-doc] to discover how.

## Retrieve Items from Array

When you write out a list on a notepad, you typically write each item on its
own line. Whether or not the list is explicitly numbered, the list has a
numbering scheme based on the default sequence of the lines on the paper (top
to bottom, left to right).

Just like the items in our notepad lists, elements in an `Array` are associated
with a number that represents their order. In programming, this number is
called an **index**. While humans typically start their lists at "1", `Array`s
begin their indexes at `0` (zero). So, the first item in an `Array` will always
be "at index `0`". If we have an `Array` of famous (fictional) cats:

```ruby
famous_cats = ["Cheshire Cat", "Puss in Boots", "Garfield"]
```

The `"Cheshire Cat"` is at index `0` in the `Array`, `"Puss in Boots"` is  a index
`1`, and `"Garfield"` is at index `2`. Indexes will always be *one less* than
the **count**.

To access one of these items in the `famous_cats` `Array`, we can type the name of
the `Array` immediately followed by the relevant index number wrapped in square
brackets (`[]`).

```ruby
famous_cats =  ["Cheshire Cat", "Puss in Boots", "Garfield"]

famous_cats[1]
#=> "Puss in Boots"

famous_cats[0]
#=> "Cheshire Cat"

famous_cats[2]
#=> "Garfield"
```

We can also access `Array` elements by using negative index numbers. The last item
of an `Array` is considered to be stored at an index of `-1`. Let's give it a
shot:

```ruby
famous_cats[-1]
#=>  "Garfield"
```

## Identify Elements in an Array Based on Their Index Number

To discover the index number of an element within an `Array`, we can use the
`.index()` method. Calling `.index()` on an `Array` with an argument inside the
parentheses will return the *first* index number of an element matching that
argument. If no elements match the argument, then this method will return `nil`.

```ruby
famous_cats = ["Cheshire Cat", "Puss in Boots", "Garfield"]

famous_cats.index("Puss in Boots")
#=> 1

famous_cats.index("Maru")
#=> nil
```

This is not an operation you will perform very often. `Array`s are used to store
data and usually you will use the index number of an item to access it, not the
other way around.

### A Note on Index Numbers

What happens when we try to access the element stored in an index that doesn't
exist? In other words, let's say we have our `famous_cats` `Array` that contains
three elements. That means that our `Array` contains an element at indexes `0`,
`1`, and `2`. What happens if we try to access an element at index `3`? An index
element that doesn't exist.

Let's take a look:

```ruby
famous_cats[3]
#=> nil
```

It returns `nil`!

## Conclusion

Create, retrieve, update, and delete operations are fundamental to working with
data. Being able to quickly manipulate and read data out of them is vital to
successful programming.

## Resources

<iframe width="560" height="315" src="https://www.youtube.com/embed/W0Q_AyfolRw" frameborder="0" allowfullscreen></iframe><p><a href="https://www.youtube.com/watch?v=W0Q_AyfolRw">Intro to Ruby Arrays</a></p>

[rb-array-doc]: http://docs.ruby-lang.org/en/2.0.0/Array.html#method-i-delete_at
