# Cells::Hamlit

Hamlit support for Cells. [Hamlit](https://github.com/k0kubun/hamlit) is a faster implementation of Haml.


## Installation

Add this line to your application's Gemfile:

```ruby
gem "cells-hamlit"
```

Note that you need [hamlit-block](https://github.com/hamlit/hamlit-block), too, for `capture` support.
This will slightly change semantics with blocks, as follows. # TODO

Add this lines to your application's Gemfile:

```ruby
gem "cells-hamlit"
gem "hamlit-block"
```

## Capture

```haml
- content = capture do
  = "takashi is king!"
```

To capture strings, the `=` directive is needed in the block.

## HTML Escaping

Cells doesn't escape except when you tell it to do. However, you may run into problems when using Rails helpers. Internally, those helpers often blindly escape. This is not Cells' fault but a design flaw in Rails.

As a first step, try this and see if it helps.

```ruby
class SongCell < Cell::ViewModel
  include ActionView::Helpers::FormHelper
  include Cell::Hamlit # include Haml _after_ AV helpers.

  # ..
end
```

If that doesn't work, [read the docs](http://trailblazer.to/gems/cells).

## Dependencies

This gem works with Tilt 1.4 and 2.0, and hence allows you to use it from Rails 3.2 upwards.
