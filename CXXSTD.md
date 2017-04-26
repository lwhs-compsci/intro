# C++ Club Standards #

These are somewhat small now but may grow. A few guidelines that are mostly my personal style.

+ I usually name things using underscores (`_`) to combine words: `this_thing`, `a_long_name_for_something`
+ I dislike the use of functions that just return private fields. (property methods) Just use a public field. 
+ Try to keep operations on data close to the data. Put operations in methods on the data if they use the data
+ Don't be afraid to break out of strict Java-esq Object oriented programming
+ Use a more functional style (don't be afraid of `std::function<>` and friends) 
+ Use std stuff as much as possible (algorithms, structures)
