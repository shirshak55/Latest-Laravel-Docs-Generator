# Helpers {#helpers}

- [Introduction](#helpers-introduction)
- [Available Methods](#helpers-available-methods)

## Introduction {#helpers-introduction}

Laravel includes a variety of global "helper" PHP functions. Many of these functions are used by the framework itself; however, you are free to use them in your own applications if you find them convenient.

## Available Methods {#helpers-available-methods}

<style>
    .collection-method-list > p {
        column-count: 3; -moz-column-count: 3; -webkit-column-count: 3;
        column-gap: 2em; -moz-column-gap: 2em; -webkit-column-gap: 2em;
    }

    .collection-method-list a {
        display: block;
    }
</style>

### Arrays & Objects

<div class="collection-method-list" markdown="1">

[array_add](#helpers-method-array-add)
[array_collapse](#helpers-method-array-collapse)
[array_divide](#helpers-method-array-divide)
[array_dot](#helpers-method-array-dot)
[array_except](#helpers-method-array-except)
[array_first](#helpers-method-array-first)
[array_flatten](#helpers-method-array-flatten)
[array_forget](#helpers-method-array-forget)
[array_get](#helpers-method-array-get)
[array_has](#helpers-method-array-has)
[array_last](#helpers-method-array-last)
[array_only](#helpers-method-array-only)
[array_pluck](#helpers-method-array-pluck)
[array_prepend](#helpers-method-array-prepend)
[array_pull](#helpers-method-array-pull)
[array_random](#helpers-method-array-random)
[array_set](#helpers-method-array-set)
[array_sort](#helpers-method-array-sort)
[array_sort_recursive](#helpers-method-array-sort-recursive)
[array_where](#helpers-method-array-where)
[array_wrap](#helpers-method-array-wrap)
[data_fill](#helpers-method-data-fill)
[data_get](#helpers-method-data-get)
[data_set](#helpers-method-data-set)
[head](#helpers-method-head)
[last](#helpers-method-last)
</div>

### Paths

<div class="collection-method-list" markdown="1">

[app_path](#helpers-method-app-path)
[base_path](#helpers-method-base-path)
[config_path](#helpers-method-config-path)
[database_path](#helpers-method-database-path)
[mix](#helpers-method-mix)
[public_path](#helpers-method-public-path)
[resource_path](#helpers-method-resource-path)
[storage_path](#helpers-method-storage-path)

</div>

### Strings

<div class="collection-method-list" markdown="1">

[\__](#helpers-method-__)
[camel_case](#helpers-method-camel-case)
[class_basename](#helpers-method-class-basename)
[e](#helpers-method-e)
[ends_with](#helpers-method-ends-with)
[kebab_case](#helpers-method-kebab-case)
[preg_replace_array](#helpers-method-preg-replace-array)
[snake_case](#helpers-method-snake-case)
[starts_with](#helpers-method-starts-with)
[str_after](#helpers-method-str-after)
[str_before](#helpers-method-str-before)
[str_contains](#helpers-method-str-contains)
[str_finish](#helpers-method-str-finish)
[str_is](#helpers-method-str-is)
[str_limit](#helpers-method-str-limit)
[Str::orderedUuid](#helpers-method-str-ordered-uuid)
[str_plural](#helpers-method-str-plural)
[str_random](#helpers-method-str-random)
[str_replace_array](#helpers-method-str-replace-array)
[str_replace_first](#helpers-method-str-replace-first)
[str_replace_last](#helpers-method-str-replace-last)
[str_singular](#helpers-method-str-singular)
[str_slug](#helpers-method-str-slug)
[str_start](#helpers-method-str-start)
[studly_case](#helpers-method-studly-case)
[title_case](#helpers-method-title-case)
[trans](#helpers-method-trans)
[trans_choice](#helpers-method-trans-choice)
[Str::uuid](#helpers-method-str-uuid)

</div>

### URLs

<div class="collection-method-list" markdown="1">

[action](#helpers-method-action)
[asset](#helpers-method-asset)
[secure_asset](#helpers-method-secure-asset)
[route](#helpers-method-route)
[secure_url](#helpers-method-secure-url)
[url](#helpers-method-url)

</div>

### Miscellaneous

<div class="collection-method-list" markdown="1">

[abort](#helpers-method-abort)
[abort_if](#helpers-method-abort-if)
[abort_unless](#helpers-method-abort-unless)
[app](#helpers-method-app)
[auth](#helpers-method-auth)
[back](#helpers-method-back)
[bcrypt](#helpers-method-bcrypt)
[blank](#helpers-method-blank)
[broadcast](#helpers-method-broadcast)
[cache](#helpers-method-cache)
[class_uses_recursive](#helpers-method-class-uses-recursive)
[collect](#helpers-method-collect)
[config](#helpers-method-config)
[cookie](#helpers-method-cookie)
[csrf_field](#helpers-method-csrf-field)
[csrf_token](#helpers-method-csrf-token)
[dd](#helpers-method-dd)
[decrypt](#helpers-method-decrypt)
[dispatch](#helpers-method-dispatch)
[dispatch_now](#helpers-method-dispatch-now)
[dump](#helpers-method-dump)
[encrypt](#helpers-method-encrypt)
[env](#helpers-method-env)
[event](#helpers-method-event)
[factory](#helpers-method-factory)
[filled](#helpers-method-filled)
[info](#helpers-method-info)
[logger](#helpers-method-logger)
[method_field](#helpers-method-method-field)
[now](#helpers-method-now)
[old](#helpers-method-old)
[optional](#helpers-method-optional)
[policy](#helpers-method-policy)
[redirect](#helpers-method-redirect)
[report](#helpers-method-report)
[request](#helpers-method-request)
[rescue](#helpers-method-rescue)
[resolve](#helpers-method-resolve)
[response](#helpers-method-response)
[retry](#helpers-method-retry)
[session](#helpers-method-session)
[tap](#helpers-method-tap)
[today](#helpers-method-today)
[throw_if](#helpers-method-throw-if)
[throw_unless](#helpers-method-throw-unless)
[trait_uses_recursive](#helpers-method-trait-uses-recursive)
[transform](#helpers-method-transform)
[validator](#helpers-method-validator)
[value](#helpers-method-value)
[view](#helpers-method-view)
[with](#helpers-method-with)

</div>

## Method Listing {#helpers-method-listing}

<style>
    #collection-method code {
        font-size: 14px;
    }

    #collection-method:not(.first-collection-method) {
        margin-top: 50px;
    }
</style>

## Arrays & Objects {#helpers-arrays}

#### `array_add()` {#collection-method .first-collection-method} {#helpers-method-array-add}

The `array_add` function adds a given key / value pair to an array if the given key doesn't already exist in the array:

    $array = array_add(['name' => 'Desk'], 'price', 100);

    // ['name' => 'Desk', 'price' => 100]

#### `array_collapse()` {#collection-method} {#helpers-method-array-collapse}

The `array_collapse` function collapses an array of arrays into a single array:

    $array = array_collapse([[1, 2, 3], [4, 5, 6], [7, 8, 9]]);

    // [1, 2, 3, 4, 5, 6, 7, 8, 9]

#### `array_divide()` {#collection-method} {#helpers-method-array-divide}

The `array_divide` function returns two arrays, one containing the keys, and the other containing the values of the given array:

    [$keys, $values] = array_divide(['name' => 'Desk']);

    // $keys: ['name']

    // $values: ['Desk']

#### `array_dot()` {#collection-method} {#helpers-method-array-dot}

The `array_dot` function flattens a multi-dimensional array into a single level array that uses "dot" notation to indicate depth:

    $array = ['products' => ['desk' => ['price' => 100]]];

    $flattened = array_dot($array);

    // ['products.desk.price' => 100]

#### `array_except()` {#collection-method} {#helpers-method-array-except}

The `array_except` function removes the given key / value pairs from an array:

    $array = ['name' => 'Desk', 'price' => 100];

    $filtered = array_except($array, ['price']);

    // ['name' => 'Desk']

#### `array_first()` {#collection-method} {#helpers-method-array-first}

The `array_first` function returns the first element of an array passing a given truth test:

    $array = [100, 200, 300];

    $first = array_first($array, function ($value, $key) {
        return $value >= 150;
    });

    // 200

A default value may also be passed as the third parameter to the method. This value will be returned if no value passes the truth test:

    $first = array_first($array, $callback, $default);

#### `array_flatten()` {#collection-method} {#helpers-method-array-flatten}

The `array_flatten` function flattens a multi-dimensional array into a single level array:

    $array = ['name' => 'Joe', 'languages' => ['PHP', 'Ruby']];

    $flattened = array_flatten($array);

    // ['Joe', 'PHP', 'Ruby']

#### `array_forget()` {#collection-method} {#helpers-method-array-forget}

The `array_forget` function removes a given key / value pair from a deeply nested array using "dot" notation:

    $array = ['products' => ['desk' => ['price' => 100]]];

    array_forget($array, 'products.desk');

    // ['products' => []]

#### `array_get()` {#collection-method} {#helpers-method-array-get}

The `array_get` function retrieves a value from a deeply nested array using "dot" notation:

    $array = ['products' => ['desk' => ['price' => 100]]];

    $price = array_get($array, 'products.desk.price');

    // 100

The `array_get` function also accepts a default value, which will be returned if the specific key is not found:

    $discount = array_get($array, 'products.desk.discount', 0);

    // 0

#### `array_has()` {#collection-method} {#helpers-method-array-has}

The `array_has` function checks whether a given item or items exists in an array using "dot" notation:

    $array = ['product' => ['name' => 'Desk', 'price' => 100]];

    $contains = array_has($array, 'product.name');

    // true

    $contains = array_has($array, ['product.price', 'product.discount']);

    // false

#### `array_last()` {#collection-method} {#helpers-method-array-last}

The `array_last` function returns the last element of an array passing a given truth test:

    $array = [100, 200, 300, 110];

    $last = array_last($array, function ($value, $key) {
        return $value >= 150;
    });

    // 300

A default value may be passed as the third argument to the method. This value will be returned if no value passes the truth test:

    $last = array_last($array, $callback, $default);

#### `array_only()` {#collection-method} {#helpers-method-array-only}

The `array_only` function returns only the specified key / value pairs from the given array:

    $array = ['name' => 'Desk', 'price' => 100, 'orders' => 10];

    $slice = array_only($array, ['name', 'price']);

    // ['name' => 'Desk', 'price' => 100]

#### `array_pluck()` {#collection-method} {#helpers-method-array-pluck}

The `array_pluck` function retrieves all of the values for a given key from an array:

    $array = [
        ['developer' => ['id' => 1, 'name' => 'Taylor']],
        ['developer' => ['id' => 2, 'name' => 'Abigail']],
    ];

    $names = array_pluck($array, 'developer.name');

    // ['Taylor', 'Abigail']

You may also specify how you wish the resulting list to be keyed:

    $names = array_pluck($array, 'developer.name', 'developer.id');

    // [1 => 'Taylor', 2 => 'Abigail']

#### `array_prepend()` {#collection-method} {#helpers-method-array-prepend}

The `array_prepend` function will push an item onto the beginning of an array:

    $array = ['one', 'two', 'three', 'four'];

    $array = array_prepend($array, 'zero');

    // ['zero', 'one', 'two', 'three', 'four']

If needed, you may specify the key that should be used for the value:

    $array = ['price' => 100];

    $array = array_prepend($array, 'Desk', 'name');

    // ['name' => 'Desk', 'price' => 100]

#### `array_pull()` {#collection-method} {#helpers-method-array-pull}

The `array_pull` function returns and removes a key / value pair from an array:

    $array = ['name' => 'Desk', 'price' => 100];

    $name = array_pull($array, 'name');

    // $name: Desk

    // $array: ['price' => 100]

A default value may be passed as the third argument to the method. This value will be returned if the key doesn't exist:

    $value = array_pull($array, $key, $default);

#### `array_random()` {#collection-method} {#helpers-method-array-random}

The `array_random` function returns a random value from an array:

    $array = [1, 2, 3, 4, 5];

    $random = array_random($array);

    // 4 - (retrieved randomly)

You may also specify the number of items to return as an optional second argument. Note that providing this argument will return an array, even if only one item is desired:

    $items = array_random($array, 2);

    // [2, 5] - (retrieved randomly)

#### `array_set()` {#collection-method} {#helpers-method-array-set}

The `array_set` function sets a value within a deeply nested array using "dot" notation:

    $array = ['products' => ['desk' => ['price' => 100]]];

    array_set($array, 'products.desk.price', 200);

    // ['products' => ['desk' => ['price' => 200]]]

#### `array_sort()` {#collection-method} {#helpers-method-array-sort}

The `array_sort` function sorts an array by its values:

    $array = ['Desk', 'Table', 'Chair'];

    $sorted = array_sort($array);

    // ['Chair', 'Desk', 'Table']

You may also sort the array by the results of the given Closure:

    $array = [
        ['name' => 'Desk'],
        ['name' => 'Table'],
        ['name' => 'Chair'],
    ];

    $sorted = array_values(array_sort($array, function ($value) {
        return $value['name'];
    }));

    /*
        [
            ['name' => 'Chair'],
            ['name' => 'Desk'],
            ['name' => 'Table'],
        ]
    */

#### `array_sort_recursive()` {#collection-method} {#helpers-method-array-sort-recursive}

The `array_sort_recursive` function recursively sorts an array using the `sort` function:

    $array = [
        ['Roman', 'Taylor', 'Li'],
        ['PHP', 'Ruby', 'JavaScript'],
    ];

    $sorted = array_sort_recursive($array);

    /*
        [
            ['Li', 'Roman', 'Taylor'],
            ['JavaScript', 'PHP', 'Ruby'],
        ]
    */

#### `array_where()` {#collection-method} {#helpers-method-array-where}

The `array_where` function filters an array using the given Closure:

    $array = [100, '200', 300, '400', 500];

    $filtered = array_where($array, function ($value, $key) {
        return is_string($value);
    });

    // [1 => '200', 3 => '400']

#### `array_wrap()` {#collection-method} {#helpers-method-array-wrap}

The `array_wrap` function wraps the given value in an array. If the given value is already an array it will not be changed:

    $string = 'Laravel';

    $array = array_wrap($string);

    // ['Laravel']

If the given value is null, an empty array will be returned:

    $nothing = null;

    $array = array_wrap($nothing);

    // []

#### `data_fill()` {#collection-method} {#helpers-method-data-fill}

The `data_fill` function sets a missing value within a nested array or object using "dot" notation:

    $data = ['products' => ['desk' => ['price' => 100]]];

    data_fill($data, 'products.desk.price', 200);

    // ['products' => ['desk' => ['price' => 100]]]

    data_fill($data, 'products.desk.discount', 10);

    // ['products' => ['desk' => ['price' => 100, 'discount' => 10]]]

This function also accepts asterisks as wildcards and will fill the target accordingly:

    $data = [
        'products' => [
            ['name' => 'Desk 1', 'price' => 100],
            ['name' => 'Desk 2'],
        ],
    ];

    data_fill($data, 'products.*.price', 200);

    /*
        [
            'products' => [
                ['name' => 'Desk 1', 'price' => 100],
                ['name' => 'Desk 2', 'price' => 200],
            ],
        ]
    */

#### `data_get()` {#collection-method} {#helpers-method-data-get}

The `data_get` function retrieves a value from a nested array or object using "dot" notation:

    $data = ['products' => ['desk' => ['price' => 100]]];

    $price = data_get($data, 'products.desk.price');

    // 100

The `data_get` function also accepts a default value, which will be returned if the specified key is not found:

    $discount = data_get($data, 'products.desk.discount', 0);

    // 0

#### `data_set()` {#collection-method} {#helpers-method-data-set}

The `data_set` function sets a value within a nested array or object using "dot" notation:

    $data = ['products' => ['desk' => ['price' => 100]]];

    data_set($data, 'products.desk.price', 200);

    // ['products' => ['desk' => ['price' => 200]]]

This function also accepts wildcards and will set values on the target accordingly:

    $data = [
        'products' => [
            ['name' => 'Desk 1', 'price' => 100],
            ['name' => 'Desk 2', 'price' => 150],
        ],
    ];

    data_set($data, 'products.*.price', 200);

    /*
        [
            'products' => [
                ['name' => 'Desk 1', 'price' => 200],
                ['name' => 'Desk 2', 'price' => 200],
            ],
        ]
    */

By default, any existing values are overwritten. If you wish to only set a value if it doesn't exist, you may pass `false` as the third argument:

    $data = ['products' => ['desk' => ['price' => 100]]];

    data_set($data, 'products.desk.price', 200, false);

    // ['products' => ['desk' => ['price' => 100]]]

#### `head()` {#collection-method} {#helpers-method-head}

The `head` function returns the first element in the given array:

    $array = [100, 200, 300];

    $first = head($array);

    // 100

#### `last()` {#collection-method} {#helpers-method-last}

The `last` function returns the last element in the given array:

    $array = [100, 200, 300];

    $last = last($array);

    // 300

## Paths {#helpers-paths}

#### `app_path()` {#collection-method} {#helpers-method-app-path}

The `app_path` function returns the fully qualified path to the `app` directory. You may also use the `app_path` function to generate a fully qualified path to a file relative to the application directory:

    $path = app_path();

    $path = app_path('Http/Controllers/Controller.php');

#### `base_path()` {#collection-method} {#helpers-method-base-path}

The `base_path` function returns the fully qualified path to the project root. You may also use the `base_path` function to generate a fully qualified path to a given file relative to the project root directory:

    $path = base_path();

    $path = base_path('vendor/bin');

#### `config_path()` {#collection-method} {#helpers-method-config-path}

The `config_path` function returns the fully qualified path to the `config` directory. You may also use the `config_path` function to generate a fully qualified path to a given file within the application's configuration directory:

    $path = config_path();

    $path = config_path('app.php');

#### `database_path()` {#collection-method} {#helpers-method-database-path}

The `database_path` function returns the fully qualified path to the `database` directory. You may also use the `database_path` function to generate a fully qualified path to a given file within the database directory:

    $path = database_path();

    $path = database_path('factories/UserFactory.php');

#### `mix()` {#collection-method} {#helpers-method-mix}

The `mix` function returns the path to a [versioned Mix file](#{{version}}/mix):

    $path = mix('css/app.css');

#### `public_path()` {#collection-method} {#helpers-method-public-path}

The `public_path` function returns the fully qualified path to the `public` directory. You may also use the `public_path` function to generate a fully qualified path to a given file within the public directory:

    $path = public_path();

    $path = public_path('css/app.css');

#### `resource_path()` {#collection-method} {#helpers-method-resource-path}

The `resource_path` function returns the fully qualified path to the `resources` directory. You may also use the `resource_path` function to generate a fully qualified path to a given file within the resources directory:

    $path = resource_path();

    $path = resource_path('assets/sass/app.scss');

#### `storage_path()` {#collection-method} {#helpers-method-storage-path}

The `storage_path` function returns the fully qualified path to the `storage` directory. You may also use the `storage_path` function to generate a fully qualified path to a given file within the storage directory:

    $path = storage_path();

    $path = storage_path('app/file.txt');

## Strings {#helpers-strings}

#### `__()` {#collection-method} {#helpers-method-__}

The `__` function translates the given translation string or translation key using your [localization files](#{{version}}/localization):

    echo __('Welcome to our application');

    echo __('messages.welcome');

If the specified translation string or key does not exist, the `__` function will return the given value. So, using the example above, the `__` function would return `messages.welcome` if that translation key does not exist.

#### `camel_case()` {#collection-method} {#helpers-method-camel-case}

The `camel_case` function converts the given string to `camelCase`:

    $converted = camel_case('foo_bar');

    // fooBar

#### `class_basename()` {#collection-method} {#helpers-method-class-basename}

The `class_basename` returns the class name of the given class with the class' namespace removed:

    $class = class_basename('Foo\Bar\Baz');

    // Baz

#### `e()` {#collection-method} {#helpers-method-e}

The `e` function runs PHP's `htmlspecialchars` function with the `double_encode` option set to `true` by default:

    echo e('<html>foo</html>');

    // &lt;html&gt;foo&lt;/html&gt;

#### `ends_with()` {#collection-method} {#helpers-method-ends-with}

The `ends_with` function determines if the given string ends with the given value:

    $result = ends_with('This is my name', 'name');

    // true

#### `kebab_case()` {#collection-method} {#helpers-method-kebab-case}

The `kebab_case` function converts the given string to `kebab-case`:

    $converted = kebab_case('fooBar');

    // foo-bar

#### `preg_replace_array()` {#collection-method} {#helpers-method-preg-replace-array}

The `preg_replace_array` function replaces a given pattern in the string sequentially using an array:

    $string = 'The event will take place between :start and :end';

    $replaced = preg_replace_array('/:[a-z_]+/', ['8:30', '9:00'], $string);

    // The event will take place between 8:30 and 9:00

#### `snake_case()` {#collection-method} {#helpers-method-snake-case}

The `snake_case` function converts the given string to `snake_case`:

    $converted = snake_case('fooBar');

    // foo_bar

#### `starts_with()` {#collection-method} {#helpers-method-starts-with}

The `starts_with` function determines if the given string begins with the given value:

    $result = starts_with('This is my name', 'This');

    // true

#### `str_after()` {#collection-method} {#helpers-method-str-after}

The `str_after` function returns everything after the given value in a string:

    $slice = str_after('This is my name', 'This is');

    // ' my name'

#### `str_before()` {#collection-method} {#helpers-method-str-before}

The `str_before` function returns everything before the given value in a string:

    $slice = str_before('This is my name', 'my name');

    // 'This is '

#### `str_contains()` {#collection-method} {#helpers-method-str-contains}

The `str_contains` function determines if the given string contains the given value (case sensitive):

    $contains = str_contains('This is my name', 'my');

    // true

You may also pass an array of values to determine if the given string contains any of the values:

    $contains = str_contains('This is my name', ['my', 'foo']);

    // true

#### `str_finish()` {#collection-method} {#helpers-method-str-finish}

The `str_finish` function adds a single instance of the given value to a string if it does not already end with the value:

    $adjusted = str_finish('this/string', '/');

    // this/string/

    $adjusted = str_finish('this/string/', '/');

    // this/string/

#### `str_is()` {#collection-method} {#helpers-method-str-is}

The `str_is` function determines if a given string matches a given pattern. Asterisks may be used to indicate wildcards:

    $matches = str_is('foo*', 'foobar');

    // true

    $matches = str_is('baz*', 'foobar');

    // false

#### `str_limit()` {#collection-method} {#helpers-method-str-limit}

The `str_limit` function truncates the given string at the specified length:

    $truncated = str_limit('The quick brown fox jumps over the lazy dog', 20);

    // The quick brown fox...

You may also pass a third argument to change the string that will be appended to the end:

    $truncated = str_limit('The quick brown fox jumps over the lazy dog', 20, ' (...)');

    // The quick brown fox (...)

#### `Str::orderedUuid()` {#collection-method} {#helpers-method-str-ordered-uuid}

The `Str::orderedUuid` method generates a "timestamp first" UUID that may be efficiently stored in an indexed database column:

    use Illuminate\Support\Str;

    return (string) Str::orderedUuid();

#### `str_plural()` {#collection-method} {#helpers-method-str-plural}

The `str_plural` function converts a string to its plural form. This function currently only supports the English language:

    $plural = str_plural('car');

    // cars

    $plural = str_plural('child');

    // children

You may provide an integer as a second argument to the function to retrieve the singular or plural form of the string:

    $plural = str_plural('child', 2);

    // children

    $plural = str_plural('child', 1);

    // child

#### `str_random()` {#collection-method} {#helpers-method-str-random}

The `str_random` function generates a random string of the specified length. This function uses PHP's `random_bytes` function:

    $random = str_random(40);

#### `str_replace_array()` {#collection-method} {#helpers-method-str-replace-array}

The `str_replace_array` function replaces a given value in the string sequentially using an array:

    $string = 'The event will take place between ? and ?';

    $replaced = str_replace_array('?', ['8:30', '9:00'], $string);

    // The event will take place between 8:30 and 9:00

#### `str_replace_first()` {#collection-method} {#helpers-method-str-replace-first}

The `str_replace_first` function replaces the first occurrence of a given value in a string:

    $replaced = str_replace_first('the', 'a', 'the quick brown fox jumps over the lazy dog');

    // a quick brown fox jumps over the lazy dog

#### `str_replace_last()` {#collection-method} {#helpers-method-str-replace-last}

The `str_replace_last` function replaces the last occurrence of a given value in a string:

    $replaced = str_replace_last('the', 'a', 'the quick brown fox jumps over the lazy dog');

    // the quick brown fox jumps over a lazy dog

#### `str_singular()` {#collection-method} {#helpers-method-str-singular}

The `str_singular` function converts a string to its singular form. This function currently only supports the English language:

    $singular = str_singular('cars');

    // car

    $singular = str_singular('children');

    // child

#### `str_slug()` {#collection-method} {#helpers-method-str-slug}

The `str_slug` function generates a URL friendly "slug" from the given string:

    $slug = str_slug('Laravel 5 Framework', '-');

    // laravel-5-framework

#### `str_start()` {#collection-method} {#helpers-method-str-start}

The `str_start` function adds a single instance of the given value to a string if it does not already start with the value:

    $adjusted = str_start('this/string', '/');

    // /this/string

    $adjusted = str_start('/this/string', '/');

    // /this/string

#### `studly_case()` {#collection-method} {#helpers-method-studly-case}

The `studly_case` function converts the given string to `StudlyCase`:

    $converted = studly_case('foo_bar');

    // FooBar

#### `title_case()` {#collection-method} {#helpers-method-title-case}

The `title_case` function converts the given string to `Title Case`:

    $converted = title_case('a nice title uses the correct case');

    // A Nice Title Uses The Correct Case

#### `trans()` {#collection-method} {#helpers-method-trans}

The `trans` function translates the given translation key using your [localization files](#{{version}}/localization):

    echo trans('messages.welcome');

If the specified translation key does not exist, the `trans` function will return the given key. So, using the example above, the `trans` function would return `messages.welcome` if the translation key does not exist.

#### `trans_choice()` {#collection-method} {#helpers-method-trans-choice}

The `trans_choice` function translates the given translation key with inflection:

    echo trans_choice('messages.notifications', $unreadCount);

If the specified translation key does not exist, the `trans_choice` function will return the given key. So, using the example above, the `trans_choice` function would return `messages.notifications` if the translation key does not exist.

#### `Str::uuid()` {#collection-method} {#helpers-method-str-uuid}

The `Str::uuid` method generates a UUID (version 4):

    use Illuminate\Support\Str;

    return (string) Str::uuid();

## URLs {#helpers-urls}

#### `action()` {#collection-method} {#helpers-method-action}

The `action` function generates a URL for the given controller action. You do not need to pass the full namespace of the controller. Instead, pass the controller class name relative to the `App\Http\Controllers` namespace:

    $url = action('HomeController@index');

If the method accepts route parameters, you may pass them as the second argument to the method:

    $url = action('UserController@profile', ['id' => 1]);

#### `asset()` {#collection-method} {#helpers-method-asset}

The `asset` function generates a URL for an asset using the current scheme of the request (HTTP or HTTPS):

    $url = asset('img/photo.jpg');

#### `secure_asset()` {#collection-method} {#helpers-method-secure-asset}

The `secure_asset` function generates a URL for an asset using HTTPS:

    $url = secure_asset('img/photo.jpg');

#### `route()` {#collection-method} {#helpers-method-route}

The `route` function generates a URL for the given named route:

    $url = route('routeName');

If the route accepts parameters, you may pass them as the second argument to the method:

    $url = route('routeName', ['id' => 1]);

By default, the `route` function generates an absolute URL. If you wish to generate a relative URL, you may pass `false` as the third argument:

    $url = route('routeName', ['id' => 1], false);

#### `secure_url()` {#collection-method} {#helpers-method-secure-url}

The `secure_url` function generates a fully qualified HTTPS URL to the given path:

    $url = secure_url('user/profile');

    $url = secure_url('user/profile', [1]);

#### `url()` {#collection-method} {#helpers-method-url}

The `url` function generates a fully qualified URL to the given path:

    $url = url('user/profile');

    $url = url('user/profile', [1]);

If no path is provided, a `Illuminate\Routing\UrlGenerator` instance is returned:

    $current = url()->current();

    $full = url()->full();

    $previous = url()->previous();

## Miscellaneous {#helpers-miscellaneous}

#### `abort()` {#collection-method} {#helpers-method-abort}

The `abort` function throws [an HTTP exception](#{{version}}/errors-http-exceptions) which will be rendered by the [exception handler](#{{version}}/errors-the-exception-handler):

    abort(403);

You may also provide the exception's response text and custom response headers:

    abort(403, 'Unauthorized.', $headers);

#### `abort_if()` {#collection-method} {#helpers-method-abort-if}

The `abort_if` function throws an HTTP exception if a given boolean expression evaluates to `true`:

    abort_if(! Auth::user()->isAdmin(), 403);

Like the `abort` method, you may also provide the exception's response text as the third argument and an array of custom response headers as the fourth argument.

#### `abort_unless()` {#collection-method} {#helpers-method-abort-unless}

The `abort_unless` function throws an HTTP exception if a given boolean expression evaluates to `false`:

    abort_unless(Auth::user()->isAdmin(), 403);

Like the `abort` method, you may also provide the exception's response text as the third argument and an array of custom response headers as the fourth argument.

#### `app()` {#collection-method} {#helpers-method-app}

The `app` function returns the [service container](#{{version}}/container) instance:

    $container = app();

You may pass a class or interface name to resolve it from the container:

    $api = app('HelpSpot\API');

#### `auth()` {#collection-method} {#helpers-method-auth}

The `auth` function returns an [authenticator](#{{version}}/authentication) instance. You may use it instead of the `Auth` facade for convenience:

    $user = auth()->user();

If needed, you may specify which guard instance you would like to access:

    $user = auth('admin')->user();

#### `back()` {#collection-method} {#helpers-method-back}

The `back` function generates a [redirect HTTP response](#{{version}}/responses-redirects) to the user's previous location:

    return back($status = 302, $headers = [], $fallback = false);

    return back();

#### `bcrypt()` {#collection-method} {#helpers-method-bcrypt}

The `bcrypt` function [hashes](#{{version}}/hashing) the given value using Bcrypt. You may use it as an alternative to the `Hash` facade:

    $password = bcrypt('my-secret-password');

#### `broadcast()` {#collection-method} {#helpers-method-broadcast}

The `broadcast` function [broadcasts](#{{version}}/broadcasting) the given [event](#{{version}}/events) to its listeners:

    broadcast(new UserRegistered($user));

#### `blank()` {#collection-method} {#helpers-method-blank}

The `blank` function returns whether the given value is "blank":

    blank('');
    blank('   ');
    blank(null);
    blank(collect());

    // true

    blank(0);
    blank(true);
    blank(false);

    // false

For the inverse of `blank`, see the [`filled`](#helpers-method-filled) method.

#### `cache()` {#collection-method} {#helpers-method-cache}

The `cache` function may be used to get values from the [cache](#{{version}}/cache). If the given key does not exist in the cache, an optional default value will be returned:

    $value = cache('key');

    $value = cache('key', 'default');

You may add items to the cache by passing an array of key / value pairs to the function. You should also pass the number of minutes or duration the cached value should be considered valid:

    cache(['key' => 'value'], 5);

    cache(['key' => 'value'], now()->addSeconds(10));

#### `class_uses_recursive()` {#collection-method} {#helpers-method-class-uses-recursive}

The `class_uses_recursive` function returns all traits used by a class, including traits used by all of its parent classes:

    $traits = class_uses_recursive(App\User::class);

#### `collect()` {#collection-method} {#helpers-method-collect}

The `collect` function creates a [collection](#{{version}}/collections) instance from the given value:

    $collection = collect(['taylor', 'abigail']);

#### `config()` {#collection-method} {#helpers-method-config}

The `config` function gets the value of a [configuration](#{{version}}/configuration) variable. The configuration values may be accessed using "dot" syntax, which includes the name of the file and the option you wish to access. A default value may be specified and is returned if the configuration option does not exist:

    $value = config('app.timezone');

    $value = config('app.timezone', $default);

You may set configuration variables at runtime by passing an array of key / value pairs:

    config(['app.debug' => true]);

#### `cookie()` {#collection-method} {#helpers-method-cookie}

The `cookie` function creates a new [cookie](#{{version}}/requests-cookies) instance:

    $cookie = cookie('name', 'value', $minutes);

#### `csrf_field()` {#collection-method} {#helpers-method-csrf-field}

The `csrf_field` function generates an HTML `hidden` input field containing the value of the CSRF token. For example, using [Blade syntax](#{{version}}/blade):

    {{ csrf_field() }}

#### `csrf_token()` {#collection-method} {#helpers-method-csrf-token}

The `csrf_token` function retrieves the value of the current CSRF token:

    $token = csrf_token();

#### `dd()` {#collection-method} {#helpers-method-dd}

The `dd` function dumps the given variables and ends execution of the script:

    dd($value);

    dd($value1, $value2, $value3, ...);

If you do not want to halt the execution of your script, use the [`dump`](#helpers-method-dump) function instead.

#### `decrypt()` {#collection-method} {#helpers-method-decrypt}

The `decrypt` function decrypts the given value using Laravel's [encrypter](#{{version}}/encryption):

    $decrypted = decrypt($encrypted_value);

#### `dispatch()` {#collection-method} {#helpers-method-dispatch}

The `dispatch` function pushes the given [job](#{{version}}/queues-creating-jobs) onto the Laravel [job queue](#{{version}}/queues):

    dispatch(new App\Jobs\SendEmails);

#### `dispatch_now()` {#collection-method} {#helpers-method-dispatch-now}

The `dispatch_now` function runs the given [job](#{{version}}/queues-creating-jobs) immediately and returns the value from its `handle` method:

    $result = dispatch_now(new App\Jobs\SendEmails);

#### `dump()` {#collection-method} {#helpers-method-dump}

The `dump` function dumps the given variables:

    dump($value);

    dump($value1, $value2, $value3, ...);

If you want to stop executing the script after dumping the variables, use the [`dd`](#helpers-method-dd) function instead.

#### `encrypt()` {#collection-method} {#helpers-method-encrypt}

The `encrypt` function encrypts the given value using Laravel's [encrypter](#{{version}}/encryption):

    $encrypted = encrypt($unencrypted_value);

#### `env()` {#collection-method} {#helpers-method-env}

The `env` function retrieves the value of an [environment variable](#{{version}}/configuration-environment-configuration) or returns a default value:

    $env = env('APP_ENV');

    // Returns 'production' if APP_ENV is not set...
    $env = env('APP_ENV', 'production');

> {note} If you execute the `config:cache` command during your deployment process, you should be sure that you are only calling the `env` function from within your configuration files. Once the configuration has been cached, the `.env` file will not be loaded and all calls to the `env` function will return `null`.

#### `event()` {#collection-method} {#helpers-method-event}

The `event` function dispatches the given [event](#{{version}}/events) to its listeners:

    event(new UserRegistered($user));

#### `factory()` {#collection-method} {#helpers-method-factory}

The `factory` function creates a model factory builder for a given class, name, and amount. It can be used while [testing](#{{version}}/database-testing-writing-factories) or [seeding](#{{version}}/seeding-using-model-factories):

    $user = factory(App\User::class)->make();

#### `filled()` {#collection-method} {#helpers-method-filled}

The `filled` function returns whether the given value is not "blank":

    filled(0);
    filled(true);
    filled(false);

    // true

    filled('');
    filled('   ');
    filled(null);
    filled(collect());

    // false

For the inverse of `filled`, see the [`blank`](#helpers-method-blank) method.

#### `info()` {#collection-method} {#helpers-method-info}

The `info` function will write information to the [log](#{{version}}/errors-logging):

    info('Some helpful information!');

An array of contextual data may also be passed to the function:

    info('User login attempt failed.', ['id' => $user->id]);

#### `logger()` {#collection-method} {#helpers-method-logger}

The `logger` function can be used to write a `debug` level message to the [log](#{{version}}/errors-logging):

    logger('Debug message');

An array of contextual data may also be passed to the function:

    logger('User has logged in.', ['id' => $user->id]);

A [logger](#{{version}}/errors-logging) instance will be returned if no value is passed to the function:

    logger()->error('You are not allowed here.');

#### `method_field()` {#collection-method} {#helpers-method-method-field}

The `method_field` function generates an HTML `hidden` input field containing the spoofed value of the form's HTTP verb. For example, using [Blade syntax](#{{version}}/blade):

    <form method="POST">
        {{ method_field('DELETE') }}
    </form>

#### `now()` {#collection-method} {#helpers-method-now}

The `now` function creates a new `Illuminate\Support\Carbon` instance for the current time:

    $now = now();

#### `old()` {#collection-method} {#helpers-method-old}

The `old` function [retrieves](#{{version}}/requests-retrieving-input) an [old input](#{{version}}/requests-old-input) value flashed into the session:

    $value = old('value');

    $value = old('value', 'default');

#### `optional()` {#collection-method} {#helpers-method-optional}

The `optional` function accepts any argument and allows you to access properties or call methods on that object. If the given object is `null`, properties and methods will return `null` instead of causing an error:

    return optional($user->address)->street;

    {!! old('name', optional($user)->name) !!}

The `optional` function also accepts a Closure as its second argument. The Closure will be invoked if the value provided as the first argument is not null:

    return optional(User::find($id), function ($user) {
        return new DummyUser;
    });

#### `policy()` {#collection-method} {#helpers-method-policy}

The `policy` method retrieves a [policy](#{{version}}/authorization-creating-policies) instance for a given class:

    $policy = policy(App\User::class);

#### `redirect()` {#collection-method} {#helpers-method-redirect}

The `redirect` function returns a [redirect HTTP response](#{{version}}/responses-redirects), or returns the redirector instance if called with no arguments:

    return redirect($to = null, $status = 302, $headers = [], $secure = null);

    return redirect('/home');

    return redirect()->route('route.name');

#### `report()` {#collection-method} {#helpers-method-report}

The `report` function will report an exception using your [exception handler](#{{version}}/errors-the-exception-handler)'s `report` method:

    report($e);

#### `request()` {#collection-method} {#helpers-method-request}

The `request` function returns the current [request](#{{version}}/requests) instance or obtains an input item:

    $request = request();

    $value = request('key', $default);

#### `rescue()` {#collection-method} {#helpers-method-rescue}

The `rescue` function executes the given Closure and catches any exceptions that occur during its execution. All exceptions that are caught will be sent to your [exception handler](#{{version}}/errors-the-exception-handler)'s `report` method; however, the request will continue processing:

    return rescue(function () {
        return $this->method();
    });

You may also pass a second argument to the `rescue` function. This argument will be the "default" value that should be returned if an exception occurs while executing the Closure:

    return rescue(function () {
        return $this->method();
    }, false);

    return rescue(function () {
        return $this->method();
    }, function () {
        return $this->failure();
    });

#### `resolve()` {#collection-method} {#helpers-method-resolve}

The `resolve` function resolves a given class or interface name to its instance using the [service container](#{{version}}/container):

    $api = resolve('HelpSpot\API');

#### `response()` {#collection-method} {#helpers-method-response}

The `response` function creates a [response](#{{version}}/responses) instance or obtains an instance of the response factory:

    return response('Hello World', 200, $headers);

    return response()->json(['foo' => 'bar'], 200, $headers);

#### `retry()` {#collection-method} {#helpers-method-retry}

The `retry` function attempts to execute the given callback until the given maximum attempt threshold is met. If the callback does not throw an exception, its return value will be returned. If the callback throws an exception, it will automatically be retried. If the maximum attempt count is exceeded, the exception will be thrown:

    return retry(5, function () {
        // Attempt 5 times while resting 100ms in between attempts...
    }, 100);

#### `session()` {#collection-method} {#helpers-method-session}

The `session` function may be used to get or set [session](#{{version}}/session) values:

    $value = session('key');

You may set values by passing an array of key / value pairs to the function:

    session(['chairs' => 7, 'instruments' => 3]);

The session store will be returned if no value is passed to the function:

    $value = session()->get('key');

    session()->put('key', $value);

#### `tap()` {#collection-method} {#helpers-method-tap}

The `tap` function accepts two arguments: an arbitrary `$value` and a Closure. The `$value` will be passed to the Closure and then be returned by the `tap` function. The return value of the Closure is irrelevant:

    $user = tap(User::first(), function ($user) {
        $user->name = 'taylor';

        $user->save();
    });

If no Closure is passed to the `tap` function, you may call any method on the given `$value`. The return value of the method you call will always be `$value`, regardless of what the method actually returns in its definition. For example, the Eloquent `update` method typically returns an integer. However, we can force the method to return the model itself by chaining the `update` method call through the `tap` function:

    $user = tap($user)->update([
        'name' => $name,
        'email' => $email,
    ]);

#### `today()` {#collection-method} {#helpers-method-today}

The `today` function creates a new `Illuminate\Support\Carbon` instance for the current date:

    $today = today();

#### `throw_if()` {#collection-method} {#helpers-method-throw-if}

The `throw_if` function throws the given exception if a given boolean expression evaluates to `true`:

    throw_if(! Auth::user()->isAdmin(), AuthorizationException::class);

    throw_if(
        ! Auth::user()->isAdmin(),
        AuthorizationException::class,
        'You are not allowed to access this page'
    );

#### `throw_unless()` {#collection-method} {#helpers-method-throw-unless}

The `throw_unless` function throws the given exception if a given boolean expression evaluates to `false`:

    throw_unless(Auth::user()->isAdmin(), AuthorizationException::class);

    throw_unless(
        Auth::user()->isAdmin(),
        AuthorizationException::class,
        'You are not allowed to access this page'
    );

#### `trait_uses_recursive()` {#collection-method} {#helpers-method-trait-uses-recursive}

The `trait_uses_recursive` function returns all traits used by a trait:

    $traits = trait_uses_recursive(\Illuminate\Notifications\Notifiable::class);

#### `transform()` {#collection-method} {#helpers-method-transform}

The `transform` function executes a `Closure` on a given value if the value is not [blank](#helpers-method-blank) and returns the result of the `Closure`:

    $callback = function ($value) {
        return $value * 2;
    };

    $result = transform(5, $callback);

    // 10

A default value or `Closure` may also be passed as the third parameter to the method. This value will be returned if the given value is blank:

    $result = transform(null, $callback, 'The value is blank');

    // The value is blank

#### `validator()` {#collection-method} {#helpers-method-validator}

The `validator` function creates a new [validator](#{{version}}/validation) instance with the given arguments. You may use it instead of the `Validator` facade for convenience:

    $validator = validator($data, $rules, $messages);

#### `value()` {#collection-method} {#helpers-method-value}

The `value` function returns the value it is given. However, if you pass a `Closure` to the function, the `Closure` will be executed then its result will be returned:

    $result = value(true);

    // true

    $result = value(function () {
        return false;
    });

    // false

#### `view()` {#collection-method} {#helpers-method-view}

The `view` function retrieves a [view](#{{version}}/views) instance:

    return view('auth.login');

#### `with()` {#collection-method} {#helpers-method-with}

The `with` function returns the value it is given. If a `Closure` is passed as the second argument to the function, the `Closure` will be executed and its result will be returned:

    $callback = function ($value) {
        return (is_numeric($value)) ? $value * 2 : 0;
    };

    $result = with(5, $callback);

    // 10

    $result = with(null, $callback);

    // 0

    $result = with(5, null);

    // 5
