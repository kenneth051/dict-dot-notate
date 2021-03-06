[![Build Status](https://travis-ci.org/kenneth051/dict-dot-notate.svg?branch=develop)](https://travis-ci.org/kenneth051/dict-dot-notate) [![Coverage Status](https://coveralls.io/repos/github/kenneth051/dict-dot-notate/badge.svg?branch=add-badge)](https://coveralls.io/github/kenneth051/dict-dot-notate?branch=add-badge)

# dict_dot_notate

dict_dot_notate turns nested dictionary keys to dotted strings with their corresponding values into a basic dictionary. 

Installation

    pip install dict-dot-notate
            
Usage

    from dot_notate.dot import dict_dot_notate

Example

    data = {
    "obj": "obj",
    "nested_once": {"first": "first"},
    "nested_twice": {
        "twice": {"inner_nest": {"second": "second"}}
    },
    "nested_thrice": {
        "thrice": {"second_nest": {"tripple_nest": {"tripple": "thrice"}, "three": "three"}}
    }
    }

call the relevant method to convert our dict 

        result = dict_dot_notate(data)

output


      {
        'obj': 'obj',
        'nested_once.first': 'first',
        'nested_twice.twice.inner_nest.second': 'second',
        'nested_thrice.thrice.second_nest.tripple_nest.tripple': 'thrice', 
        'nested_thrice.thrice.second_nest.three': 'three'
        }

**If a dict passed in has a list value, Then the output will be as below**

Example

    data = {
    "obj": "obj",
    "nested_once": {"first": "first"},
    "nested_twice": {
        "twice": {"inner_nest": [1, 2, 3, 4, 5]}
    }
    }
    
conversion

    result = dict_dot_notate(data)

output

    {
    'obj': 'obj',
    'nested_once.first': 'first',
    'nested_twice.twice.inner_nest': [1, 2, 3, 4, 5]
    }


**Don't pass in a list of dictionaries.**
