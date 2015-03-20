# auto_set

[![Build Status](https://travis-ci.org/felipediesel/auto_set.svg?branch=master)](https://travis-ci.org/felipediesel/auto_set)
[![Coverage Status](https://coveralls.io/repos/felipediesel/auto_set/badge.svg?branch=master)](https://coveralls.io/r/felipediesel/auto_set?branch=master)
[![Code Climate](https://codeclimate.com/github/felipediesel/auto_set/badges/gpa.svg)](https://codeclimate.com/github/felipediesel/auto_set)

auto_set provides automatic incrementation for a integer or string fields in Rails.

## Installation

You can use auto_set as a gem in Rails 4.

To use the gem version, put the following gem requirement in your `Gemfile`:

    gem "auto_set"


## Usage

To work with a auto increment column you used to do sometihng like this in your model:

    before_create :set_code
    def set_code
      max_code = Operation.maximum(:code)
      self.code = max_code.to_i + 1
    end

Looks fine, but not when you need to do it over and over again. In fact auto_set does it under the cover.

All you need to do is this:

    auto_set

And your code field will be incremented


## Customizing

So you have a different column or need a scope. auto_set provides options. You can use it like this:

    auto_set column: :letter, scope: [:account_id, :job_id], initial: 'C', force: true

* column: the column that will be incremented. Can be integer os string (default: code)
* scope: you can define columns that will be scoped and you can use as many as you want (default: nil)
* initial: initial value of column (default: 1)
* force: you can set a value before create and auto_set will not change that, but if you do want this, set force to true (default: false)


## Compatibility

Tested with Rails 4.0.13 in Ruby 2.0.0

## License

MIT License. Copyright 2011 29sul Tecnologia da Informação <http://www.29sul.com.br/>
