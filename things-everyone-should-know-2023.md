# WordPress "Things Everyone Should Know" in 2023 (Back-end)

A repository containing links/information about what a developer should know if he wants to develop with WordPress in 2022, irrespective of their company's specific. The idea is to not go into arcane topics or things that very few people use, but rather consolidate all the topics that nearly each company seems to touch on and/or use heavily.

I chose not to include things such as 3rd-party plugins, because, when it comes to agencies, unless you're a "PSD to WP" agency, you don't generally use page builders, instead, you build themes without that overhead or simply use Gutenberg. Again, these are very specific to each agency, then to each plugin itself, but you should know a bit about how a page builder works: what controls it offers you, how they (sometimes) short-circuits template-loading, how to use them as an alternative to the Customizer and so on. Generally speaking, there isn't that much depth to them and you can get up-to-speed within a few days.

---

_To note, these are tools/paradigms that one should irrespective of their seniority._

## Tooling

[Composer](https://getcomposer.org/):
- You should know how to work with libraries, the simple add/remove commands.
- You should know how semantic versioning works, as to not create conflicts within the project, as well as be able to release your packages and create issues for others.
- You should know about PHP's limitations with auto-loading and working around two libraries who might depend on the same, but different version (third) of a library.

[PHPStan/Psalm/Phan](https://psalm.dev/):
_Admittedly, this is up to each companies' choice, and the tools, while having a lot of in common, do other different things that some others can't do. At the end of the day, you want to know about static/strong typing, because that's what these tools are helping you with_
- Knowledge about generics is heavily appreciated, but almost never used within WP projects.
- You should know about complex return types.
- You should know when to type something and when no to, alternatively, you should also understand why "typing everything is better".

[Git](https://git-scm.com/)
There's too much to cover here, but any developer, be them junior or senior, should know how to use Git, then move on to Github-specific things such as PRs.

[PHPCS](https://github.com/squizlabs/PHP_CodeSniffer)
Every project needs to have strict rules about its naming, indentation and so on. There are packages that respect WordPress standards and you can just load them in.

[PHPUnit](https://phpunit.de/index.html)
No need to talk about this one. Just the fact that you're able to write simple tests for your core functions, ensuring that, no matter what changes come through your code, it will still work, goes a long way. There's no need to know about advanced testing when it comes to WordPress, unless you're working on complex things. Worth mentioning that nearly all companies who work on WP projects use some form of CI (continuous integration), and PHPUnit will always be in that suite.

[Intellisense or "Intelligent Code"](https://code.visualstudio.com/docs/editor/intellisense)
I chose to include VSCode, because it tends to be the most popular code editor *overall*, however, within the PHP industry, looking at configuration files and soruce-code, PHPStorm seems to be as popular. Both have nearly the same features, with PHPStorm being better geared towards PHP development (native, nice support for xDebug, auto-loading of classes from the `vendor` folder, as well as other folders, so that the project operates within a "context" and knows about functions such as `add_action`, even if they're not defined within the project). All in all:
- You should have smart auto-complete.
- You should be able to peek inside a function's definition, to see what it does/what its parameters are, etc.
- You should be able to get real-time errors that pertain to typings.
- You should get most errors in your code editor, so you don't have to run the code just for that.

The above points are the bare minimum that any developer should have.

[Debug Bar](https://wordpress.org/plugins/debug-bar/)
Self-explanatory. You want to be able to see query hits/misses, the request done and so on.

[Query Monitor](https://wordpress.org/plugins/query-monitor/)
You should be very familiary with the Query Monitor, as it shows thins such as Hooks (who fired them and from where), HTTP API calls and so on. Both `Debug Bar` and `Query Monitor` can be replaced by `xDebug`, but it's just nicer to have them in the browser for when your tests have passed and the code editor doesn't scream at you, but something might go wrong.


## Libraries

[The Service Container](https://laravel.com/docs/9.x/container)
- No serious PHP project that's started in this day & age will forego using a service container. The ones that don't tend to use a global array where they find "objects of importance" by an unique key (usually, they're singletons too), so, a pseudo-service container, if yo uwill
- Should know about auto-wiring.
- Should know about automatic injection.

[Templating](https://laravel.com/docs/9.x/blade)
The choices are many, and while not _all_ WordPress vendors use a templating system, a lot do, and the ones that don't most likely would have too much trouble to turn all the raw `.php` code into a template file, but you should look into Laravel's templating system, as well as Symfony's and stand-alone templating systems. In essence, they all do the same.


## Concepts

[REST APIs](https://www.redhat.com/en/topics/api/what-is-a-rest-api)
While WordPress' REST API, both its default and most vendors' endpoints are simple GET/POST, when you're working with outside APIs, you will be met with a lot of jargon and concepts, to name a few:
- DELETE/PUT and how they interact with a system.
- Combining data and being familiar with tools that transform your mixed data into parameters for, say, a GET request. At the end of the day, a GET/POST request simply take some data and pass it as either parameters or a JSON body, you should have a tool to transform all of that for you and make the request, as a lot of endpoints also require headers, auth/session tokens and so on.
- Versioning. When it comes to REST APIs, you might want to keep a legacy API/endpoint going, while providing better endpoints using a new version.
- GraphQL is irrelevant, as it's not used by virtually anyone within WordPress, but it's a good concept to know about and how it differs. I don't think any project big enough to warrant the usage of GraphQL will be written in WordPress, but alas, it's good to see what problems it's trying to solve.

## WordPress' AJAX
While the REST API is here and supported in the core, it's often overkill and not indicated to create an endpoint for everything. WordPress' AJAX system is simply just a `POST/GET` request to the back-end, you should:
- Know about the referer parameter.
- Know about the (performance) limitations of AJAX within WordPress, bonus points if you learn about how to properly short-circuit it and what's causing it (the loading of all WordPress resources on each request), but this is not something you'll do unless you really need to.

## Post Meta
You should be familiar with what a post's meta is. Know that, while it's just *ahem*, "metadata", it can serve to build complex relationships between posts, relationships which can be queried. You should be able to talk about when it's better to just query a `$post` object, an idea about how to build relationships and why metadata doesn't replace the database itself (and, well, when should a meta key/value pair should be in the database). You don't have to know all this, but it's expected of WordPress juniors to at least have a grasp on the topic of databases/meta and how they can (and won't) work together.

## The `WP_Query` class/`get_post` function.
Retrieving posts is at the core of nearly everything you display on a WordPress site - you want to retrieve (a) number of posts that have this key, that are from this category and so on. You should be able to use the class/function with relative ease.

## Understanding SQL Queries, `$wpdb`
While you don't need to go into too many specifics, you should know that any query which has user input needs to be cleaned, as such, look to functions such as `prepare`, `get_results` and so on. You don't need to go hardcore. Bonus points if you know which functions automatically clean input.

Please know what is validation/sanitization.

Bonus points if you know about ORMs.

## Databases, SQL

In the last section, we talked about understanding SQL queries and the `$wpdb` object, but you also need to have a decent grasp on how a database functions, what primary keys are and so on. Basic stuff, just to understand how things tie together and how you can add your own fields. This is usually done by the most senior person within the project, but changes that warrant database updates tend to come from a lot of people writing a lot of code. You should know enough to know when to pester for a database update or if you can do your work with already-existing data.

This is what seems to currently be the "minimum amount of knowledge for a junior WordPress developer", based on analysis of hundreds of plugins/themes - big and small, private and public.

While some good years ago you could've gotten away with just knowing how to piece things together with `post_meta` and some other stuff, nowadays, it (thankfully) seems that the PHP eco-system, together with WordPress', have evolved drastically.

There are many other things that a "developer should know", but I deemed these too basic and put them under the category of "there's absolutely no way you don't know this" (such as the loop, how WordPress loads plugins/templates). This was more to serve as a list of things that any developer working with WordPress is expected to be ready to use and be somewhat comfortable with.

Hope it helps :)
