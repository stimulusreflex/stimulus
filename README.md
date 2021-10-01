StimulusReflex has no plans to change the package we're importing from.

You should continue using and importing the `stimulus` package, as there is no reason to effectively fork the library and break the entire ecosystem. Switching package names has zero positive value and is a fast-track to dependency issues. It is *deeply unfortunate* that DHH's blog post made it seem as though `upgrade == package name change` as this is simply not the case.

Please see the comment here, which has overwhelming and **unanimous** support: https://github.com/hotwired/stimulus/pull/421#issuecomment-908609584

There are [over 17,000](https://github.com/search?q=%22import+%7B+Controller+%7D+from+%27stimulus%27%22&type=code) *public* Stimulus controllers, and probably 10x that in private repos.

At the time I'm writing this, we're still waiting for [the official PR](https://github.com/hotwired/stimulus/pull/453) to be merged. Upvotes can't hurt!

In the meantime, we've set up a [hopefully temporary!] workaround that will Just Work: 
```bash
yarn add stimulus@https://github.com/stimulusreflex/stimulus/raw/master/stimulus-v3.0.0.tgz
```
You should end up with this dependency in your `package.json`:
```json
"dependencies": {
  "stimulus": "https://github.com/stimulusreflex/stimulus/raw/master/stimulus-v3.0.0.tgz"
}
```
There's no longer any need for the `@hotwired/stimulus-webpack-helpers` package, if you have it in your `package.json`.
```js
import { Application } from 'stimulus'
import { definitionsFromContext } from 'stimulus/webpack-helpers'
```
In your Stimulus controllers, you can `import { Controller } from 'stimulus'` and get back to work.

Feel free to [jump on Discord](https://discord.gg/stimulus-reflex) if you'd like to discuss further.
