## Problem:
The input is a list of names in random order. We need a function that chains elements of the list in such a way
that the last character of an name is the same as the first one of the next name. For instance:

Input: ["Raymond", "Nora", "Daniel", "Louie", "Peter", "Esteban"]

Output: ["Peter", "Raymond", "Daniel", "Louie", "Esteban", "Nora"]


Hint: There should be only one solution, so the first element is unique.

## Solution
The given problem statement is misleading. Here, we are not looking for a general-purpose function that
works with an arbitrary input. Rather, the interviewers were looking for a one-time solution for the exact
given input.

```php
<?php

$input = array("Raymond", "Nora", "Daniel", "Louie", "Peter", "Esteban");

function get_first_char($str) {
    return strtoupper($str[0]);
}

function get_last_char($str) {
    return strtoupper($str[strlen($str)-1]);
}

function get_name_by_initial($initial, $names) {
    foreach ($names as $name) {
        if ($initial == get_first_char($name)) {
            return $name;
        }
    }
    return NULL;
}

$output = [];
$output[] = "Peter";

while ($name = get_name_by_initial(get_last_char(end($output)), $input)) {
    $output[] = $name;
}

print_r($output);
```
