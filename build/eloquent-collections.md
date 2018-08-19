# Eloquent: Collections {#eloquent-collections}

- [Introduction](#eloquent-collections-introduction)
- [Available Methods](#eloquent-collections-available-methods)
- [Custom Collections](#eloquent-collections-custom-collections)

## Introduction {#eloquent-collections-introduction}

All multi-result sets returned by Eloquent are instances of the `Illuminate\Database\Eloquent\Collection` object, including results retrieved via the `get` method or accessed via a relationship. The Eloquent collection object extends the Laravel [base collection](#{{version}}/collections), so it naturally inherits dozens of methods used to fluently work with the underlying array of Eloquent models.

Of course, all collections also serve as iterators, allowing you to loop over them as if they were simple PHP arrays:

    $users = App\User::where('active', 1)->get();

    foreach ($users as $user) {
        echo $user->name;
    }

However, collections are much more powerful than arrays and expose a variety of map / reduce operations that may be chained using an intuitive interface. For example, let's remove all inactive models and gather the first name for each remaining user:

    $users = App\User::all();

    $names = $users->reject(function ($user) {
        return $user->active === false;
    })
    ->map(function ($user) {
        return $user->name;
    });

> {note} While most Eloquent collection methods return a new instance of an Eloquent collection, the `pluck`, `keys`, `zip`, `collapse`, `flatten` and `flip` methods return a [base collection](#{{version}}/collections) instance. Likewise, if a `map` operation returns a collection that does not contain any Eloquent models, it will be automatically cast to a base collection.

## Available Methods {#eloquent-collections-available-methods}

### The Base Collection

All Eloquent collections extend the base [Laravel collection](#{{version}}/collections) object; therefore, they inherit all of the powerful methods provided by the base collection class:

<style>
    #collection-method-list > p {
        column-count: 3; -moz-column-count: 3; -webkit-column-count: 3;
        column-gap: 2em; -moz-column-gap: 2em; -webkit-column-gap: 2em;
    }

    #collection-method-list a {
        display: block;
    }
</style>

<div id="collection-method-list" markdown="1">

[all](#{{version}}/collections-method-all)
[average](#{{version}}/collections-method-average)
[avg](#{{version}}/collections-method-avg)
[chunk](#{{version}}/collections-method-chunk)
[collapse](#{{version}}/collections-method-collapse)
[combine](#{{version}}/collections-method-combine)
[concat](#{{version}}/collections-method-concat)
[contains](#{{version}}/collections-method-contains)
[containsStrict](#{{version}}/collections-method-containsstrict)
[count](#{{version}}/collections-method-count)
[crossJoin](#{{version}}/collections-method-crossjoin)
[dd](#{{version}}/collections-method-dd)
[diff](#{{version}}/collections-method-diff)
[diffKeys](#{{version}}/collections-method-diffkeys)
[dump](#{{version}}/collections-method-dump)
[each](#{{version}}/collections-method-each)
[eachSpread](#{{version}}/collections-method-eachspread)
[every](#{{version}}/collections-method-every)
[except](#{{version}}/collections-method-except)
[filter](#{{version}}/collections-method-filter)
[first](#{{version}}/collections-method-first)
[flatMap](#{{version}}/collections-method-flatmap)
[flatten](#{{version}}/collections-method-flatten)
[flip](#{{version}}/collections-method-flip)
[forget](#{{version}}/collections-method-forget)
[forPage](#{{version}}/collections-method-forpage)
[get](#{{version}}/collections-method-get)
[groupBy](#{{version}}/collections-method-groupby)
[has](#{{version}}/collections-method-has)
[implode](#{{version}}/collections-method-implode)
[intersect](#{{version}}/collections-method-intersect)
[isEmpty](#{{version}}/collections-method-isempty)
[isNotEmpty](#{{version}}/collections-method-isnotempty)
[keyBy](#{{version}}/collections-method-keyby)
[keys](#{{version}}/collections-method-keys)
[last](#{{version}}/collections-method-last)
[map](#{{version}}/collections-method-map)
[mapInto](#{{version}}/collections-method-mapinto)
[mapSpread](#{{version}}/collections-method-mapspread)
[mapToGroups](#{{version}}/collections-method-maptogroups)
[mapWithKeys](#{{version}}/collections-method-mapwithkeys)
[max](#{{version}}/collections-method-max)
[median](#{{version}}/collections-method-median)
[merge](#{{version}}/collections-method-merge)
[min](#{{version}}/collections-method-min)
[mode](#{{version}}/collections-method-mode)
[nth](#{{version}}/collections-method-nth)
[only](#{{version}}/collections-method-only)
[pad](#{{version}}/collections-method-pad)
[partition](#{{version}}/collections-method-partition)
[pipe](#{{version}}/collections-method-pipe)
[pluck](#{{version}}/collections-method-pluck)
[pop](#{{version}}/collections-method-pop)
[prepend](#{{version}}/collections-method-prepend)
[pull](#{{version}}/collections-method-pull)
[push](#{{version}}/collections-method-push)
[put](#{{version}}/collections-method-put)
[random](#{{version}}/collections-method-random)
[reduce](#{{version}}/collections-method-reduce)
[reject](#{{version}}/collections-method-reject)
[reverse](#{{version}}/collections-method-reverse)
[search](#{{version}}/collections-method-search)
[shift](#{{version}}/collections-method-shift)
[shuffle](#{{version}}/collections-method-shuffle)
[slice](#{{version}}/collections-method-slice)
[sort](#{{version}}/collections-method-sort)
[sortBy](#{{version}}/collections-method-sortby)
[sortByDesc](#{{version}}/collections-method-sortbydesc)
[splice](#{{version}}/collections-method-splice)
[split](#{{version}}/collections-method-split)
[sum](#{{version}}/collections-method-sum)
[take](#{{version}}/collections-method-take)
[tap](#{{version}}/collections-method-tap)
[toArray](#{{version}}/collections-method-toarray)
[toJson](#{{version}}/collections-method-tojson)
[transform](#{{version}}/collections-method-transform)
[union](#{{version}}/collections-method-union)
[unique](#{{version}}/collections-method-unique)
[uniqueStrict](#{{version}}/collections-method-uniquestrict)
[unless](#{{version}}/collections-method-unless)
[values](#{{version}}/collections-method-values)
[when](#{{version}}/collections-method-when)
[where](#{{version}}/collections-method-where)
[whereStrict](#{{version}}/collections-method-wherestrict)
[whereIn](#{{version}}/collections-method-wherein)
[whereInStrict](#{{version}}/collections-method-whereinstrict)
[whereNotIn](#{{version}}/collections-method-wherenotin)
[whereNotInStrict](#{{version}}/collections-method-wherenotinstrict)
[zip](#{{version}}/collections-method-zip)

</div>

## Custom Collections {#eloquent-collections-custom-collections}

If you need to use a custom `Collection` object with your own extension methods, you may override the `newCollection` method on your model:

    <?php

    namespace App;

    use App\CustomCollection;
    use Illuminate\Database\Eloquent\Model;

    class User extends Model
    {
        /**
         * Create a new Eloquent Collection instance.
         *
         * @param  array  $models
         * @return \Illuminate\Database\Eloquent\Collection
         */
        public function newCollection(array $models = [])
        {
            return new CustomCollection($models);
        }
    }

Once you have defined a `newCollection` method, you will receive an instance of your custom collection anytime Eloquent returns a `Collection` instance of that model. If you would like to use a custom collection for every model in your application, you should override the `newCollection` method on a base model class that is extended by all of your models.
