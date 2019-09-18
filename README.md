# Nested Arrays Addendum

## Learning Goals

- Recognize that coordinate assignments grow nested `Array`s
- Recognize single-coordinate access of `Array`s returns an `Array`

## Introduction

Now that you've had a chance to get familiar with the basics of working with
nested `Array`s or "matrices" (the plural of "matrix"), or "AoAs," let's cover
a "funny" case.

## Recognize That Coordinate Assignments Grow Nested `Array`s

Given the following Ruby code:

```ruby
spice_rack = [
  ["Mace", "Ginger", "Marojam"],          
  ["Paprika", "Fajita Mix", "Coriander"], 
  ["Parsley", "Sage", "Rosemary"]         
]
```

You're clear now that we can update by saying `spice_rack[1][1] = "Extract of
Pizza"`. But what would happen if we said `spice_rack[1][100] = "Poodle
Dinner"`. What would `spice_rack` look like then?

***TRY IT OUT IN IRB***. We can't emphasize this behavior enough. Programmers,
when they reach head-scratchers like this, always ask IRB to teach them. Your
learning will not gel as well if you do not take this step. Don't set your
learning backwards!

As we hope you discovered, we **can** add at _any_ coordinate pair. If the
element you need add needs the inner `Array` to "grow" in order to accommodate
it, Ruby will "grow" the `Array` and fill in the "in-between" values with
`nil`.

```ruby
spice_rack = [
  ["Mace", "Ginger", "Marojam"],             
  ["Paprika", "Fajita Mix", "Coriander"],    
  ["Parsley", "Sage", "Rosemary"]            
]
spice_rack[1][10] = "Cucumber Water"
spice_rack #=> [
  ["Mace", "Ginger", "Marojam"],
  ["Paprika", "Fajita Mix", "Coriander", nil, nil, nil, nil, nil, nil, nil, "Cucumber Water"],
  ["Parsley", "Sage", "Rosemary"]
]
```

## Recognize Single-coordinate Access of `Array`s Returns an `Array`

This isn't a new fact, but some students forget that the inner `Array`s are
***still `Array`s*** upon which we can do all the usual stuff we already know
how to do on `Array`s.

As such, you can use operators like `<<` ("shovel") on an inner `Array`:

```ruby
spice_rack = [
  ["Mace", "Ginger", "Marojam"],          
  ["Paprika", "Fajita Mix", "Coriander"], 
  ["Parsley", "Sage", "Rosemary"]         
]

spice_rack[2] << "Saffron" #=> ["Parsley", "Sage", "Rosemary", "Saffron"]

spice_rack #=> [
  ["Mace", "Ginger", "Marojam"],          
  ["Paprika", "Fajita Mix", "Coriander"], 
  ["Parsley", "Sage", "Rosemary", "Saffron"]         
]
```

Similarly, if you want to replace a whole `Array` within the containing
`Array`, you can do so by using one coordinate.

```ruby
spice_rack = [
  ["Mace", "Ginger", "Marojam"],          
  ["Paprika", "Fajita Mix", "Coriander"], 
  ["Parsley", "Sage", "Rosemary"]         
]

# Spice up your life!
spice_rack[0] = ["Posh", "Scary", "Sporty", "Baby", "Ginger"]

spice_rack #=> [
  ["Posh", "Scary", "Sporty", "Baby", "Ginger"],
  ["Paprika", "Fajita Mix", "Coriander"],
  ["Parsley", "Sage", "Rosemary"]
]

```

Keep in mind, if a matrix starts off with the same number of rows and elements
("is square"), there's nothing wrong with breaking that, if you need. Ruby
won't complain.

## Conclusion

We've covered two "tangent" topics about working with nested arrays. We've seen
these ideas occasionally cause bugs for learners ("Wait, what? How did all
those `nil`s get in there?"). Or we've seen learners get stuck because they
stop thinking of inner `Array`s as the `Array`s they already know and love.
They get all tangled up in the coordinate syntax and forget what they already
know.
