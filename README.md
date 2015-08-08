<!---------------------------------------------------------------------------->
<!-- STOP, LOOK & LISTEN!                                                   -->
<!-- ====================                                                   -->
<!-- Do NOT edit this file directly since it's generated from a template    -->
<!-- file, using https://github.com/IonicaBizau/node-blah                   -->
<!--                                                                        -->
<!-- If you found a typo in documentation, fix it in the source files       -->
<!-- (`lib/*.js`) and make a pull request.                                  -->
<!--                                                                        -->
<!-- If you have any other ideas, open an issue.                            -->
<!--                                                                        -->
<!-- Please consider reading the contribution steps (CONTRIBUTING.md).      -->
<!-- * * * Thanks! * * *                                                    -->
<!---------------------------------------------------------------------------->

![git-url-parse](http://i.imgur.com/HlfMsVf.png)

# git-url-parse [![Donate now][donate-now]][paypal-donations]

A high level git url parser for common git providers.

## Installation

```sh
$ npm i git-url-parse
```

## Example

```js
// Dependencies
var GitUrlParse = require("git-url-parse");

console.log(GitUrlParse("git@github.com:IonicaBizau/node-git-url-parse.git"));
// => {
//     protocols: []
//   , port: null
//   , resource: "github.com"
//   , user: "git"
//   , pathname: "/IonicaBizau/node-git-url-parse.git"
//   , hash: ""
//   , search: ""
//   , href: "git@github.com:IonicaBizau/node-git-url-parse.git"
//   , token: ""
//   , protocol: "ssh"
//   , toString: [Function]
//   , source: "github.com"
//   , name: "node-git-url-parse"
//   , owner: "IonicaBizau"
// }

console.log(GitUrlParse("https://github.com/IonicaBizau/node-git-url-parse.git"));
// => {
//     protocols: ["https"]
//   , port: null
//   , resource: "github.com"
//   , user: ""
//   , pathname: "/IonicaBizau/node-git-url-parse.git"
//   , hash: ""
//   , search: ""
//   , href: "https://github.com/IonicaBizau/node-git-url-parse.git"
//   , token: ""
//   , protocol: "https"
//   , toString: [Function]
//   , source: "github.com"
//   , name: "node-git-url-parse"
//   , owner: "IonicaBizau"
// }

console.log(GitUrlParse("https://github.com/IonicaBizau/node-git-url-parse.git").toString("ssh"));
// => "git@github.com:IonicaBizau/node-git-url-parse.git"

console.log(GitUrlParse("git@github.com:IonicaBizau/node-git-url-parse.git").toString("https"));
// => "https://github.com/IonicaBizau/node-git-url-parse.git"

```

## Documentation

### `GitUrlParse(url)`
Parses a Git url.

#### Params
- **String** `url`: The Git url to parse.

#### Return
- **GitUrl** The `GitUrl` object containing:
 - `protocols` (Array): An array with the url protocols (usually it has one element).
 - `port` (null|Number): The domain port.
 - `resource` (String): The url domain (including subdomains).
 - `user` (String): The authentication user (usually for ssh urls).
 - `pathname` (String): The url pathname.
 - `hash` (String): The url hash.
 - `search` (String): The url querystring value.
 - `href` (String): The input url.
 - `protocol` (String): The git url protocol.
 - `token` (String): The oauth token (could appear in the https urls).
 - `source` (String): The Git provider (e.g. `"github.com"`).
 - `owner` (String): The repository owner.
 - `name` (String): The repository name.
 - `toString` (Function): A function to stringify the parsed url into another url type.
 - `organization` (String): The organization the owner belongs to. This is CloudForge specific.

### `stringify(obj, type)`
Stringifies a `GitUrl` object.

#### Params
- **GitUrl** `obj`: The parsed Git url object.
- **String** `type`: The type of the stringified url (default `obj.protocol`).

#### Return
- **String** The stringified url.

## How to contribute
Have an idea? Found a bug? See [how to contribute][contributing].

## License
[KINDLY][license] © [Ionică Bizău][website]–The [LICENSE](/LICENSE) file contains
a copy of the license.

[license]: http://ionicabizau.github.io/kindly-license/?author=Ionic%C4%83%20Biz%C4%83u%20%3Cbizauionica@gmail.com%3E&year=2015
[contributing]: /CONTRIBUTING.md
[website]: http://ionicabizau.net
[docs]: /DOCUMENTATION.md
[paypal-donations]: https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=MG98D7NPFZ3MG
[donate-now]: http://i.imgur.com/jioicaN.png