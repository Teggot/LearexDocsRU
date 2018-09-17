Getting started guide
=====================

You should start with instalation process but let me postpone that.

Instalation process
===================

some stuff

Quick language guide
====================

Variables
^^^^^^^^^

First thing first. You need to get into this specific syntax::

    10 >> age;
    # age = 10
    5. >> double value;
    # value = 5.0

Here i created 2 variables "age" and "value"
In this case "age" is dynamic so you can probably change it's value(including type) and the "value" is created with static type "double" so you can't change "value"'s type later.

Also you can use "<<" but it has only 1 time, e.g.::

    age << 10;
    # age = 10
    return << age;

Complex example
^^^^^^^^^^^^^^^

That's how it looks.
Sounds not interesting at all? I have a much more complicated statement::

    example(10), 10 >> example{1}, var, example(10) >> sum{3} >> age >> out;

Here i have some functions and a bit complex stuff but you will get into it very fast.

Importing
^^^^^^^^^

Also some stuff like importing modules::

    import IO

    # or

    from IO{
        import func out(int val):void
    }

    # or

    import func printf(string a, b):int32

Functions
^^^^^^^^^

Also you can create some functions::

    func calc(int a, int b){
        a + b >> return;
    }

    func example(double a):double{
        a*1.5 >> return;
    }

Here you have 2 functions.
There is a strange thing after "func example(double a)". ":double" means return type. By default every function returns void(nothing) and if you haven't specified return type yet, then function will detect it by itself. (specifying return type is important when you want to use recursion).

Complex "putting"
^^^^^^^^^^^^^^^^^

Here appears interesting syntax

You can "put" values into function::

    10, 5 >> calc{2} >> int some;
    # some = 15

Let's postpone "{2}" for now.

Now i'll explain how COMMA works in that context::

    10, 20 >> int a, b;
    # a = 10
    # b = 20

Here you see that first element from left is putted into first of right, 2nd in 2nd and so on.

Lets look at this example
::

    10, 20 >> calc{2} >> out; # out is imported from IO
    # 30

That "{2}" made for overloading compability. That means, when you are calling function in "put" context compiler can't find out which number of arguments you are "putting" to function. So "{2}" means that compiler must search for function with exactly 2 arguments.
Btw, if no "{}" provided, then compiler searches for function with 1 param.
    
Also you can call function like this::

    calc(10, 20) >> out;
    # 30

Extending "put" context
^^^^^^^^^^^^^^^^^^^^^^^

Also you can add new arguments to your "put" context e.g.::

    10, 20 >> calc{2}, calc(10, 20) >> calc{2} >> out;
    # 60

Casting to types
^^^^^^^^^^^^^^^^

you can cast variable to type::

    age|&int8;
    # age is casted to *int8;


If statements
^^^^^^^^^^^^^

To run code ahead you should import IO lib (as i have mentioned before).

Ifs::

    if (10 == 10){
        10 >> out;
    }else if 20 == 20{
        20 >> out;
    }else{
        30 >> out;
    }

    # or

    if (10 == 10):
        10 >> out;
    elseif 20 == 20
        20 >> out;
    else:
        30 >> out;
    endif

Loops
^^^^^

I have prepeared some different loops e.g.::

    for(0 >> int a; a <= 10; a+1>>a;){
        a >> out;
    }

    0 >> n;
    while n <= 10{
        n >> out;
        n + 1 >> n;
    }


Next steps
==========

.. toctree::
    :maxdepth: 2
    
    advanced_steps
    future_features