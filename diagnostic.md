# Ember Routing Diagnostic

Record your responses inside the fenced code blocks below each question.

1.  What are the main task(s) you perform inside the Ember Application Router,
    and what are the main task(s) you perform inside an Ember Route?

    ```md
    I think the Ember Application Router is what you call the main app directory
    in the template. It basically maps url path extensions to different routes.
    Each route basically defines a model to be used by a markup template, and the template
    which takes data from the model and can display it. The template may pass
    the data to components but it doesn't have to. When you navigate to a route,
    you display the template affiliated with that route using data in that route's
    route file.
    ```

1.  What is the command to generate a route named `boston` nested under
    `campus`?

    ```md
    ember g route campus/boston
    ```

1.  Suppose you have a nested route at the URL `/campus/boston`. How would you
    use the `link-to` helper to generate an appropriate link?

    ```md
    {{#link-to 'campus.boston' class="btn btn-default"}}Boston{{/link-to}}
    ```

1.  Explain **at least** two differences between the following two route
    definitions.

    ```js
    this.route('products', function () {
      this.route('product', { path: '/:product_id' }); // <= 👀here
    });

    this.route('product', { path: '/products/:product_id' }); // <= 👀 here
    ```

    ```md
    It looks like the main difference is that the first is defining an actual nested
    route, with 'product' being nested under 'products' while the other is defining
    a non-nested route that happens to use 'products'.

    I am not 100% sure on this, but I think the difference is that in the first case,
    you will see the 'product' template in the {{outlet}} inside of the 'products' template,
    while in the second case, you will just see a 'product' template rendered.
    ```

1.  Suppose we have the following route definition:

    ```js
    this.route('movie', { path: '/movies/:movie_id' }); // <= 👀 here
    ```

    If we navigate in the browser to `/movies/123`, how can we reference the
    value `'123'` inside a Route?

    ```md
    The value 123 is the movie_id in the params hash so: params.movie_id should work.
    I think params[movie_id] also works but I haven't tried that yet.
    ```

1.  Inside a template, how do we reference data provided by a Route?

    ```md
    The data comes from the model object in the route, so you reference it like this:

    {{#each model as |varName|}}
      do something with varName
    {{/each}}

    for a loop.

    Or you can just use like model.attribute to get specific pieces of data.
    ```
