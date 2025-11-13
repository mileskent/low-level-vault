How different kinds of expressions are categorized in [[C++]]
# lvalue
A variable
# lvalue reference
A variable reference
e.g. a function expression that returns a reference, 
a reference to an lvalue
Can be assigned to
# rvalue
Temporaries 
e.g. a literal, an concatenated expression, a function expression that returns an rvalue
Cannot be assigned to
Cannot be referenced (&), unless const referenced

# rvalue reference
denoted by &&
you would probably just see this as a function parameter, to select for only [[#rvalue]]s