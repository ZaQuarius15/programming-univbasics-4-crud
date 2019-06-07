# Array Basics: Creating, Retrieving, Updating and Deleting

## Learning Goals

- Create an array
- Add items to an array
- Remove items from an array
- Retrieve items from an array
- Identify elements in an array based on their index number
- Update Array element value using its index number

## Introduction

Conceptually, we know what arrays are and what they look like. Now we can learn
details like how to create, manipulate, and retrieve data from arrays.

## Create an Array

There are a few different ways to make a new array. You can use the _literal_
constructor or the _class_ constructor.

### The Literal Constructor

```ruby
my_array = []
```

### The Class Constructor

```ruby
my_array = Array.new
#=> []
```

**Advanced:** _Don't worry about the class constructor right now. We'll learn
much more about this later on. We're introducing it briefly here because you may
encounter this syntax in other resources._

To make an array that isn't empty, you can separate each item, known as an
_element_, by a `,` ("comma") and wrap all the elements inside `[]` ("square
brackets").

```ruby
puppies = ["bulldog", "terrier", "poodle"]
#=> ["bulldog", "terrier", "poodle"]

random_numbers = [ 2, 5, 6, 8, 30050]
#=> [ 2, 5, 6, 8, 30050]

mixed = ["this", "array", 7, 20, "has", 45, "integers", "&", "strings", 309]
#=> ["this", "array", 7, 20, "has", 45, "integers", "&", "strings", 309]
```

It is possible to create an array that contains different data types. In other
words, you could create an array like the one above that stores both strings
and integers. However, this is generally discouraged. It's best to keep your
arrays populated with only one kind of element.

Remember we're saying that arrays hold collections of similar things: band
member names, digits of a phone number, etc. Other programmers will likely
want to visit each _element_. If I'm totaling an array called `prices`, and the
`String` `"baby shark"` is inside, I'm not going to get the result I expect when
I try to add up the total of all the prices.

## Add Items to an Array

If an array is a storage container for a list of data, then we can imagine
adding and removing individual items. Let's take a look at how we can add
elements to an array.

### The Shovel Method

The **shovel** method employs the "shovel" operator (`<<`) and allows you to add
("shovel") items onto the _end_ of an array:

```ruby
famous_cats = ["lil' bub", "grumpy cat", "Maru"]

famous_cats << "nala cat"

p famous_cats
#=> ["lil' bub", "grumpy cat", "Maru", "nala cat"]
```

The shovel method (`<<`) is the preferred syntax for adding elements to an
array, however you might see other methods used in examples online.

### The `.push` Method

Calling `.push` on an array with an argument will add that element to the _end_
of the array. It has the same effect as the shovel method explained above:

```ruby
famous_cats = ["lil' bub", "grumpy cat", "Maru"]

famous_cats.push("nala cat")

p famous_cats
#=> ["lil' bub", "grumpy cat", "Maru", "nala cat"]
```

### The `.unshift` Method

To add an element to the _front_ of an array, you can call the `.unshift` method
on it with an argument of the element you wish to add:

```ruby
famous_cats = ["lil' bub", "grumpy cat", "Maru"]

famous_cats.unshift("nala cat")

p famous_cats
#=> ["nala cat", "lil' bub", "grumpy cat", "Maru"]
```

## Remove Items from an Array

### The `.pop` Method

Calling `.pop` on an array will remove the _last_ item from the _end_ of the
array. The `.pop` method will also supply the removed element as its return:

```ruby
famous_cats = ["lil' bub", "grumpy cat", "Maru"]
maru_cat = famous_cats.pop

p famous_cats
#=> ["lil' bub", "grumpy cat"]
p maru_cat
#=> Maru
```

### The `.shift` Method

Calling `.shift` on an array will remove the _first_ item from the _front_ of
the array. The `.shift` method will also supply the removed element as a return:

```ruby
famous_cats = ["lil' bub", "grumpy cat", "Maru"]
lil_bub = famous_cats.shift

p famous_cats
#=> ["grumpy cat", "Maru"]
p lil_bub
#=> lil' bub
```

**Note:** If you want to remove items that are not at the beginning or end of an
array, use the [Ruby documentation](http://docs.ruby-lang.org/en/2.0.0/Array.html#method-i-delete_at)
to figure out how.

## Retrieve Items from Array

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

The `"Cheshire Cat"` is at index `0` in the array, `"Puss in Boots"` is a index
`1`, and `"Garfield"` is at index `2`. Indexes will always be _one less_ than
the **count**.

To access one of these items in the `famous_cats` array, we can type the name of
the array immediately followed by the relevant index number wrapped in square
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

We can also access array elements by using negative index numbers. The last item
of an array is considered to be stored at an index of `-1`. Let's give it a
shot:

```ruby
famous_cats[-1]
#=> "Garfield"
```

## Identify Elements in an Array Based on Their Index Number

To discover the index number of an element within an array, we can use the
`.index()` method. Calling `.index()` on an array with an argument inside the
parentheses will return the _first_ index number of an element matching that
argument. If no elements match the argument, then this method will return `nil`.

```ruby
famous_cats = ["Cheshire Cat", "Puss in Boots", "Garfield"]

famous_cats.index("Puss in Boots")
#=> 1

famous_cats.index("Maru")
#=> nil
```

This is not an operation you will perform very often. Arrays are used to store
data and usually you will use the index number of an item to access it, not the
other way around.

### A Note on Index Numbers

What happens when we try to access the element stored in an index that doesn't
exist? In other words, let's say we have our `famous_cats` array that contains
three elements. That means that our array contains an element at indexes `0`,
`1`, and `2`. What happens if we try to access an element at index `3`? An index
element that doesn't exist.

Let's take a look:

```ruby
famous_cats[3]
#=> nil
```

It returns `nil`!

## Additional Information on Arrays

The `.push`, `.shift`, `.unshift`, and `.pop` methods are not the only methods
built-in to arrays. To read the full list, check out Ruby's
[Array documentation][docs].

No programmer knows all the methods that are built-in to Ruby's Array class.
Although it is handy to practice and become familiar with methods like `.push`,
`.shift`, `.unshift`, and `.pop`, it is entirely normal to rely on the
documentation, no matter your skill level.

## Update `Array` Element Value Using Its Index Number

Let's imagine we have an Array, but we want to update a single value in it.

```ruby
picnic_ingredients = ["wine", "jalapeños", "donkey feed"]
```

Yuck. I don't want to eat donkey feed during my picnic. We know that `"donkey
feed"` is at _index_ `2` in the `Array`. So let's change it with something more
appetizing (to humans, anyway).

```ruby
picnic_ingredients[2] = "Belgian chocolate"
=> "Belgian chocolate"
```

The return value shows the new value that was entered: `"Belgian chocolate"`.

If we now print out the `Array` using `p` we see:

```ruby
picnic_ingredients = ["wine", "jalapeños", "Belgian chocolate"]
```

## Conclusion

Create, retrieve, update, and delete operations are fundamental to working with
data. Being able to quickly manipulate and read data out of them is vital to
successful programming.

## Resources

- [Working with Arrays Video][video]

[video]: https://www.youtube.com/embed/W0Q_AyfolRw
[docs]: https://ruby-doc.org/core-2.5.1/Array.html

