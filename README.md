# Agency data

Here is a fun JSON of Dutch digital agencies to practice data transformations with

- Includes 600+ agencies (20000)
- Includes meta data like disciplines and tags

## How to use

- Just download the db.json file and include it in your project 👍

- Use the json-server package to consume this data through a REST api
  1. `git clone` this repo
  2. install dependencies with `npm install`
  3. Start the server with `npm start`, see package.json for the script

## Examples

(start the server first to make these links work)

### Agencies:

Get all agencies: [http://localhost:4000/agencies](http://localhost:4000/agencies)
Get all agencies in Amsterdam: [http://localhost:4000/agencies?city=Amsterdam](http://localhost:4000/agencies?city=Amsterdam)
Get all agencies with the tag Wordpress: [http://localhost:4000/agencies?tags_like=Wordpress](http://localhost:4000/agencies?tags_like=Wordpress)

For more info visit [https://github.com/typicode/json-server#filter](https://github.com/typicode/json-server#filter) docs

### Meta data

An object with all the branches and how many agencies work in this branch: [http://localhost:4000/branches](http://localhost:4000/branches)
An object with all the disciplines and how many agencies practice this discipline: [http://localhost:4000/disciplines](http://localhost:4000/disciplines)
An object with all the tags and how many agencies have this tag: [http://localhost:4000/tags](http://localhost:4000/tags)

- Want an array instead of this meta information instead? (so you can map over it?)

```js
async function getBranches() {
  const res = await axios.get("http://localhost:4000/branches");

  console.log(res.data);

  /*
    Object like this
    {
      "IT": 185, -> 185 agencies are in the "IT" branche
      "Reclame &amp; communicatie": 178, -> 178 agencies are in the "Reclame &amp; communicatie" branche
      "Retail": 171,
    }
    */

  // turn into an array using Object.keys!

  const branches = Object.keys(res.data);

  console.log(branches); // ["IT", "Reclame &amp; communicatie", "Retail"], now you can map all the branches
}
```
