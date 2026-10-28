# Lab Activity 11: Finish Your Own CRUD (Movie App)

## G1. Route model binding

Binding in `MovieController` needs two things: the parameter must be type-hinted with the `Movie` model, and its name must match the route segment `{movie}`, so it is written `Movie $movie`. If only the type-hint is right (for example `Movie $m`), Laravel gives me an empty `Movie` object with no error. If only the name is right (for example `$movie` with no `Movie` type), I get the raw id string back and no record.

## G2. The Delete link

The Delete link is an `<a>` tag, and a link can only send a GET request. The `movies/{movie}` address is correct, but my `destroy()` method only answers DELETE, so a GET can never reach it. Only the verb is wrong, which is why the delete only worked once I switched to a form with `@method('DELETE')`.

## G3. The second argument of old()

In my edit form, `old('title', $movie->title)` uses the movie's saved title as a fallback. Without the second argument, the form opens empty (like my Screenshot 3) because there is nothing to fall back on. With only the second argument (`$movie->title`), a rejected submit would bring back the original saved title and throw away what I typed, for example a cleared Title would reappear as "The Matrix".