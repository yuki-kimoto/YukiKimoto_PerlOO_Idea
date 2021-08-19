# Yuki Kimoto's Perl Object Oriented Ideas

This is Yuki Kimoto's Perl Object Oriented Ideas.

## Descriptor - Real Attribute

Perl has attirbute feature. This is only string which user can interporate freely.

```
# sub return value attribute
sub func : foo { }

# variable attribute
my $var : foo;

# argument attribute(this is future)
sub func ($args1 : foo) { }

```

A problem is that attribute is not for Perl Core.

At first, Perl implements real attribute. I name it descriptor temporary. Package descriptor, sub descriptor, variable descriptor.

```
sub func is foo ($args1 is foo) { }

my $var is foo;

package PackageName is foo {
  
}
```

Descriptor is only used for Perl core.


## Class Declaration

Class declaration is package syntax + Descriptor(class).

```
package Foo is class {
  
}

```

Inheritance.

```
package Foo is class extends Bar, Baz {
  
}

```

Other internal data type.

```
package PackageName is class, array {
  
}
```

## Filed declaration - has

Filed declaration is has. 

```
has FIELD_NAME;
```

What is the battle between us? That is plain old hash reference vs Moo/se's encapsulated data structure.

We accept both expressions.

```
# Internal data is plain old hash reference
has x is rw;
has y is ro;

# Internal data is encapsulated data structure(Twigil)
has $:x is rw;
has $:y is ro;
```

There are two expressions in Perl core, however much better than hundreds? 

## Method definition

Method definition is method keyword.

```
method foo () {
  
}
```

## Filed access

Field access is two types.

```
method foo ($x) {
  # Plain old hash reference
  $self->{x} = $x;
  
  # Twigil
  $:x = $x;
}
```

## Other features

Detail is maybe after this. 

Field Initialization.

Setter return value is custamized?

Is default new contructor overided?

BUILD, BUILDARGS, Role, Lazy build, Runtime type check, DEMOLISH is OK if people want to impelment them.
