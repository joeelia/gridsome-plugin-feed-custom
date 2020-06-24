# gridsome-plugin-feed

Generate an RSS, Atom, and/or JSON feed for your Gridsome site.

## Install

- `yarn add gridsome-plugin-podcast-feed`
- `npm install gridsome-plugin-podcast-feed`

## Example

```js
module.exports = {
  plugins: [
    {
      use: 'gridsome-plugin-podcast-feed',
      options: {
        contentTypes: ['Podcast'],
        // Optional: any properties you wish to set for `Feed()` constructor
        // See https://www.npmjs.com/package/feed#example for available properties
        feedOptions: {
          title: 'My Awesome Blog Feed',
          description: 'Best blog feed evah.'
        },
        // === All options after this point show their default values ===
        // Optional; opt into which feeds you wish to generate, and set their output path
        // Optional: the maximum number of items to include in your feed
        maxItems: 25,
        // Optional: an array of properties passed to `Feed.addItem()` that will be parsed for
        // URLs in HTML (ensures that URLs are full `http` URLs rather than site-relative).
        // To disable this functionality, set to `null`.
        htmlFields: ['description', 'content'],
        // Optional: if you wish to enforce trailing slashes for site URLs
        enforceTrailingSlashes: false,
        // Optional: a method that accepts a node and returns true (include) or false (exclude)
        // Example: only past-dated nodes: `filterNodes: (node) => node.date <= new Date()`
        filterNodes: (node) => true,
        // Optional: a method that accepts a node and returns an object for `Feed.addItem()`
        // See https://www.npmjs.com/package/feed#example for available properties
        // NOTE: `date` field MUST be a Javascript `Date` object
        nodeToFeedItem: (node) => ({
          title: node.title,
          date: node.date || node.fields.date,
          content: node.content
        })
      }
    }
  ]
}
```
