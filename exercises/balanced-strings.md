# Balanced strings

A string containing grouping symbols `{}[]()` is said to be balanced if every open symbol `{[(` has a matching closed symbol `]}` and the substrings before, after and between each pair of symbols is also balanced. The empty string is considered as balanced.

For example: `{[][]}({})` is balanced, while `][`, `([)]`, `{`, `{(}{}` are not.

Implement the following method:

```java
public static boolean isBalanced(String str) {
    ...
}
```

`isBalanced` returns `true` if `str` is balanced according to the rules explained above. Otherwise, it returns `false`.

Use the coverage criteria studied in classes as follows:

1. Use input space partitioning to design an initial set of inputs. Explain below the characteristics and partition blocks you identified.
2. Evaluate the statement coverage of the test cases designed in the previous step. If needed, add new test cases to increase the coverage. Describe below what you did in this step.
3. If you have in your code any predicate that uses more than two boolean operators check if the test cases written so far satisfy *Base Choice Coverage*. If needed add new test cases. Describe below how you evaluated the logic coverage and the new test cases you added.
4. Use PIT to evaluate the test suite you have so far. Describe below the mutation score and the live mutants. Add new test cases or refactor the existing ones to achieve a high mutation score.

Write below the actions you took on each step and the results you obtained.
Use the project in [tp3-balanced-strings](../code/tp3-balanced-strings) to complete this exercise.

## Answer

1. First of all, we found one partition block: String is null or not. After that, we needed to check if strings with 0 grouping symbols are correctly handled, so a second block we created: Number of grouping symbols: 0 orr >=1. After that, we needed to test every possibility conerning the number or order of symbols. The most important characteristics are if grouping symbols are even or odd, and if they are in the right order (opening then closing symbols). Two other blocks can then be created based on thoses characteristics: number of grouping symbols: even or odd, and grouping symbols in order: true or false. One last step was refining the characteristic about odd symbols. There can be more opening or more closing symbols, resulting in different behaviours from the method. We created one last block: more closing symbols: true or false.
 -String is null: true or false;
 -Number of grouping symbols equals 0: true or false;
 -Number of grouping symbols is even: true or false;
 -More closing symbols: true or false;
 -All grouping symbols in order: true or false;
 
 The tests we decided to make are based on those different input values:
 ```
 null
"string"
"[[()string{}]]"
"[[)(string{}]]"
"(string"
"[string"
"{string"
")string"
"]string"
"}string"
"(string}{"
"string}{)"
 ```
