.. _properties-manifesto:

#######################
When to use properties?
#######################

Sources:

* PEP8_
* `Programming in the .NET environment`_ pages 241-2.

In summary, I think that properties are OK iff (if and only if):

* they are simply used to make an attribute read only OR
* they reproduce attribute access with run time check (raising errors)
  *but no change to* the attribute value being set AND
* the get and set code is very short (in the order of 5 lines) AND
* the get and set do not set off demanding computation (think ipython
  tab completion) AND
* the get and set methods are private by convention or otherwise AND
* accessing the property has no unexpected side effects

So, specifically, these are OK::

    class C(object):
    def __init__(self, arg1, arg2):
        self._arg1= arg1
        self._arg2 = None
        self.arg2 = arg2

    # just read only
    @property
    def arg1(self):
        return self._arg1

    # just checks but does not change input
    # uses a nice pattern to hide the get/set methods
    def arg2():
        def fget(self):
            return self._arg2
        def fset(self, arg2):
            if arg2 not in (1,2,3,4):
                raise ValueError('arg should be in range 1..4')
            self._arg2 = arg2
        doc = 'argument 2'
        return locals()
    arg2 = property(**arg2())

But, this would be a bit goofy::

    class D(object):
    def __init__(self, arg3):
        self._arg3 = None
        self.arg3 = arg3  # OK so far - as a above

    def get_arg3(self):  # ouch, public getter, more than one way to do it
        return self._arg3

    def set_arg3(self, arg3): # ditto above, and
        self._arg3 = arg3 + 1  # odd...

    arg3 = property(get_arg3, set_arg3, '', 'argument 3')

Giving the following odd results::

    d = D(3)
    print d.arg3 # gives 4
    d.arg3 = 3
    print d.arg3 # 4 again

This is a silly example, but I've written property setters that do
fairly complex transformations in the ``set_...``  method, resulting in
oddnesses like the above.

**********
Background
**********

This is a summary of `Programming in the .NET environment`_ pages 241-2.

A property looks like an attribute.  Developers instinctively treat them as if
they were simple attributes.  Thus, they do not expect getting or setting a
field to visibly perform some operation.  By 'visibly', I mean that the property
does something to the object for which the effects can be seen by the developer.

So, you'd probably prefer a method to a property in the following situations:

* If the method converts the input to something else - that the developer can
  see in the object interface.  For example if ``obj.prop = var ; obj.prop ==
  var`` is not ``True`` this would be confusing.
* If the get or set for the property takes a long time or uses lots of CPU.
  Consider also ipython tab completion.  If pressing tab sets of a 5 second file
  access, that is not good.
* If the get method changes the public interface of object in some way.  For
  example, this would be confusing::

    >>> obj.foo
    'spam'
    >>> obj.bar = 'eggs'
    >>> obj.foo
    'spam and eggs'

* As a subset of the above, you'd prefer a method if the get method had a
  different effect when called a second or third time.
* If the get or set method had different effects depending on previous calls to
  other parts of the object interface.
* If the thing you ``set`` is mutable, but the thing you ``get`` is not.  For
  example::

    >>> obj.bar = [1, 2]
    >>> baz = obj.bar
    >>> baz[0] = 3
    >>> obj.bar
    [1, 2]

  would be confusing.  Obviously this comes up for returning - say - copies of
  arrays.

The book also points out that if you return something iterable and reasonably
expensive to create with your ``get`` call, and then iterate over it, without
realizing the expense, it could get bad.  As in::

    for i in range(len(obj.arr_property)):
        j += obj.arr_property[i] # big cost for each i

where ``obj.arr_property`` is an expensive thing like a copy.

****
PEP8
****

Stuff relevant to properties:

    - For simple public data attributes, it is best to expose just the
       attribute name, without complicated accessor/mutator methods.  Keep in
       mind that Python provides an easy path to future enhancement, should
       you find that a simple data attribute needs to grow functional
       behavior.  In that case, use properties to hide functional
       implementation behind simple data attribute access syntax.

       Note 1: Properties only work on new-style classes.

       Note 2: Try to keep the functional behavior side-effect free, although
       side-effects such as caching are generally fine.

       Note 3: Avoid using properties for computationally expensive
       operations; the attribute notation makes the caller believe
       that access is (relatively) cheap.

.. _Programming in the .NET Environment:  http://www.amazon.com/exec/obidos/tg/detail/-/0201770180/qid=1042505176
