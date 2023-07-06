---
tags: [course, postman]
aliases: []
description:
public: true
dg-publish: true
created: 2023-04-17
---

# postman fundamentals course pluralsight

## Links

- [Postman JavaScript reference | Postman Learning Center](https://learning.postman.com/docs/writing-scripts/script-references/postman-sandbox-api-reference/)
- [Scripting in Postman | Postman Learning Center](https://learning.postman.com/docs/writing-scripts/intro-to-scripts/)
- [Test script examples | Postman Learning Center](https://learning.postman.com/docs/writing-scripts/script-references/test-examples/#getting-started-with-tests)
- [Test script examples | Postman Learning Center](https://learning.postman.com/docs/writing-scripts/script-references/test-examples/#validating-response-structure)
- [28 | Postman Tutorials | Monitors | Monitoring your #api - YouTube](https://www.youtube.com/watch?v=g5O3eF4xR30)

## Postman basics

Clone repo <https://github.com/taylonr/postman>

Dependencies

```
npm install

```

Run server

```bash
cd C:\Users\MaksimZinovev\repos\postman
npm run start:dev
to restart at any time, enter `rs`

```

Open in browser: <http://localhost:3000/landing>

## Visualiser in Postman

Add code in Tests tab

```js
var template = `
    <table bgcolor="#FFFFFF">
        <tr>
            <th>ID</th>
            <th>Title</th>
            <th>Author</th>
            <th>ISBN</th>
        </tr>

        {{#each response}}
            <tr>
                <td>{{id}}</td>
                <td>{{title}}</td>
                <td>{{author}}</td>
                <td>{{isbn}}</td>
            </tr>
        {{/each}}
    </table>
`;

// Set visualizer
pm.visualizer.set(template, {
    // Pass the response body parsed as JSON as `data`
    response: pm.response.json()
});


```

## Using history section

## Changing GET requests to POST

Authentication required: admin

Body: no

## Preset headers

Example:

- required headers
  - username
  - password
  - business unit
  - client id
  - authorization

## Header presets

Request > Headers > Presets > Add new preset

Now create new request > Headers > Presets > Your preset.

## Environments

create
replace hardcoded values with environment variable
duplicate
view icon (top right)

## Import

```
http://localhost:3000/ui

```

Go to browser
Create new book
Network tab > Copy as cURL
Postman > Import > Raw test > paste > Import

## Proxy

Postman > Bottom right > Capture requests > Enable proxy > <https://learning.postman.com/docs/sending-requests/capturing-request-data/capturing-https-traffic/#installing-openssl-on-windows>

Postman >  Bottom right > Capture requests > Start capture

Install Chrome extension

Go to browser and interaact with web app

## Generating  code

Send request
Right side of window > Code snippet

## Sync

Allows to sync between multiple computers

## Pre-built tests

Send request
Tests tab  
Snippets
Response > Test results

## Test syntax

pm
.info
.globals
.environment
.assertions

Status code is 200

```js
pm.test("Status code name has string", () => {
    pm.response.to.have.status("OK");
});

```

## Basic tests

```js
pm.test("All books should have a title", () => {
    const books = pm.response.json();
    pm.expect(books.every(book => {
        return book.title !== undefined;
    })).to.be.true;
});

```

Refactored

```js

const titleIsDefined = (book) => {
    return book.title !== undefined;
}

pm.test("All books should have a title", () => {
    const books = pm.response.json();
    pm.expect(books.every(titleIsDefined)).to.be.true;
});

```

## Using other libraries

```js

const moment  = require('moment');

obj = {
    "title": `${pm.variables.replaceIn('{{$randomWords}}')}`,
    "author": `${pm.variables.replaceIn('{{$randomFirstName}}')}`,
    "isbn": `${pm.variables.replaceIn('{{$randomInt}}')}743351Y`,
    "releaseDate": `${moment().format('YYYY-MM-DD')}`
}

pm.collectionVariables.set('book', JSON.stringify(obj));

```

Test

```js

const moment = require('moment'); 
pm.test('Create date is equal to today', () => {
    const data = pm.response.json();
    pm.expect(moment(data.createdAt).format('MM/DD/YYYY'))
    .to.eql(moment().format('MM/DD/YYYY'))
})

```

## Using dynamic variables to generate fake data in pre-request script

```js
let randomFirstName = '{{$randomFirstName}}'
pm.collectionVariables.set('user_name_rand',`${pm.variables.replaceIn(randomFirstName)}`);

```

## Using dynamic variables to generate fake data in request body

Example body demonstrating how to use dynamic variables to generate fake data

```JSON
{
    "email": "troytiru+pm{{$randomInt}}@gmail.com", 
    "firstName": "{{$randomFirstName}}",
    "lastName": "{{$randomLastName}}",
    "householdId": {{householdId}}
}

```

## Creating collections

Create collection and add request.

POST <http://localhost:3000/households>

```cURL

curl --location 'http://localhost:3000/households' \
--header 'Content-Type: application/json' \
--header 'G-TOKEN: ROM831ESV' \
--data '{
    "name": "Max Household"
}'

```

Create users request
POST

```curl

curl --location 'http://localhost:3000/users' \
--header 'Content-Type: application/json' \
--header 'G-TOKEN: ROM831ESV' \
--data-raw '{
    "email": "troytiru+pm07@gmail.com", 
    "firstName": "Max1",
    "lastName": "Zin1",
    "householdId": 1
}'

```

Add book to whishlist

POST

```curl

curl --location 'http://localhost:3000/wishlists/1/books/1' \
--header 'Content-Type: application/json' \
--header 'G-TOKEN: ROM831ESV' \
--data-raw '{
    "email": "troytiru+pm07@gmail.com", 
    "firstName": "Max1",
    "lastName": "Zin1",
    "householdId": 1
}'

```

GET household books

```curl

curl --location 'http://localhost:3000/households/1/wishlistBooks' \
--header 'Content-Type: application/json' \
--header 'G-TOKEN: ROM831ESV' \
--data ''

```

To set Variable

1. Send request
2. Tests > Snippets > Set global variable

## Collection runner  

Can be used to run multiple requests in sequence

## Using variables

Add variable "host": "<http://localhost:3000/users>"

## Pre-request scripts

Pre-request script can set up state of request before run.

```js
const users = [
    {
        email: "taylorn@gmail.com",
        firstName: "Nate",
        lastName: "Taylor"
    },
        {
        email: "jon@mailinator.com",
        firstName: "Jonathan",
        lastName: "Edwards"
    },
        {
        email: "brooks@gmail.com",
        firstName: "Thomas",
        lastName: "Brook"
    },
        {
        email: "samt@gmail.com",
        firstName: "Sami",
        lastName: "Tailwind"
    }
]

// Get one user 

const user = _.sample(users);

pm.globals.set("firstName", user.firstName);
pm.globals.set("lasttName", user.lastName);
pm.globals.set("email", user.email);


```

Body

```json

{
    "email": "{{email}}", 
    "firstName": "{{firstName}}",
    "lastName": "{{lastName}}",
    "householdId": {{householdId}}
}
```

## Data files - data driven tests

1. Go to  request body and create raw json request:

Prerequisites:

1. Create json file and save in "datafiles" folder

```json

{
    "title": "{{title}}",
    "author": "{{author}}",
    "isbn": "{{isbn}}",
    "releaseDate": "{{publicationDate}}"
}

```

2. Select collection > Run > Run configuration >
   1. Iterations > 2
   2. Select file > select json file
   3. Click preview
   4. Save responses > enabled
3. If the number of iteration is less than number of records in data file, then last record will be used.

## Initializing test data, test structure example

Basic flow

1. Set up variables
2. Create users
3. Add books
4. Clean up data

## Set up variables

Can use 1st request to set up variables in pre-request script

Example for getting list of books

```js

pm.globals.set('numberOfUsers', 2);
pm.globals.set('currentUserCounts', 0);

pm.globals.set('numberOfWhishListsAdds', 4);
pm.globals.set('currentWhishListCount', 0);


pm.globals.set('wishlistIds', []);


/// Get existing books 


const getBooks = {
    url: `http://${pm.environment.get("host")}/books`,
    method: 'GET',
    header: 'G-TOKEN:ROM831ESV'
}

pm.sendRequest(getBooks, (err, books) => {
    const ids = _.map(books.json(),
        (book) => {
            return book.id;
        });
    pm.globals.set("bookIds", ids)
})


```

## Refactor loop over users

Prerequest script

data file:

```json
// households.json
[
  {
    "users": [
      {
        "email": "taylonr@gmail.com",
        "firstName": "Nate",
        "lastName": "Taylor"
      },
      {
        "email": "charles@mailinator.com",
        "firstName": "Charles",
        "lastName": "Spurgeon"
      },
      {
        "email": "jon@mailinator.com",
        "firstName": "Jonathan",
        "lastName": "Edwards"
      },
      {
        "email": "cs@mailinator.com",
        "firstName": "C.S.",
        "lastName": "Lewis"
      }
    ]
  }
]

```

```js
// POST {{host}}/users
// data file will be included in test run
// it is used to randomly create user
// Inside of scripts when you want to access the data file, you need to use "data" property

const  users = data.users; 
const user = _.sample(users);

pm.globals.set("email", user.email);
pm.globals.set("firstNamel", user.firstName);
pm.globals.set("lastName", user.lastName);


```

Body

```json
{
    "email": "{{email}}", 
    "firstName": "{{firstName}}",
    "lastName": "{{lastName}}",
    "householdId": {{householdId}}
}
```

```js
// Test

const ids = pm.globals.get("wishlistIds");
ids.push(pm.response.json().wishlistId);
pm.globals.set("wishlistIds", ids);

let userCount = pm.globals.get("currentUserCount", userCount);
if(userCount < pm.globals("numberOfUsers")) {
    postman.setNextRequest("create user");
} else  {
    postman.setNextRequest("add book to user")
}

pm.test("Status code is 201", function () {
    pm.response.to.have.status(201);
});

```

## Refactor loop over wishlists

rerequest script

```js
// {{host}}/wishlists/{{wishlistId}}/books/{{bookId}}

const books = pm.globals.get("bookIds");
pm.globals.set("bookId", _.sample(bookIds));

const wishlistIds = pm.globals.get("wishlistIds");
pm.globals.set("wishlistId", _.sample(wishlistIds));

```

Body

```json

{}
```

```js
// Test
pm.test("Status code is 204", function () {
    pm.response.to.have.status(204);
});

let whishListCount = pm.globals.get("currentWhishListCount");
whishListCount++;
pm.globals.set("currentWhishListCount", whishListCount);
if(whishListCount < pm.globals.get("numberOfWhishListsAdds")) {
    postman.setNextRequest("add book to user");
} else  {
    postman.setNextRequest("get household books")
}
```

## Tear down

```js

// Test 

pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

// Clean up variables to not pollute list of variables between test runs

pm.globals.unset("numberOfUsers");
pm.globals.unset("currentUserCount");
pm.globals.unset("numberOfWhishListsAdds");
pm.globals.unset("currentWhishListCount");
pm.globals.unset("wishlistIds");
pm.globals.unset("bookIds");
pm.globals.unset("email");
pm.globals.unset("lastName");
pm.globals.unset("wishlistId");
pm.globals.unset("bookId");

```

## Run refactored collection

Open collection and select data file
Mark "Persisist responses"

## Compare json response with valid json

Test:

```js
const jsonData = pm.response.json();

const validJson = {
    "questions": {
        "key": "value",
    },
    "answers": {
        "key": "value"
    }
}
console.log(jsonData);
console.log(validJson);

    pm.test("Response is a JSON objects that includes valid json data", () => {
        pm.expect(jsonData).to.be.an('object').that.deep.include(validJson);
    });

```

## Testing from command line

1. Install newman

```bash  
npm insall -g newman

```

2. Download collection

Collection > right-click > export json file

3. Download environment file

Environment > right-click > export json file

4. Run collection using newman

```bash  

newman run <collection location> -e <environment location>

```

5. Add script in package.json to run postman tests

```bash  

npm run postmanTests

```

```json

  "scripts": {
    "start:dev": "nodemon app.js --ignore db.json",
    "start:test": "cross-env NODE_ENV=test PORT=3030 nodemon app.js --ignore db.test.json",
    "postmanTests": "newman run ./postman_exports/collections/Users.postman_collectionv2.json -e ./postman_exports/environments/Dev.environment.json"
  },

```

## Mock server

Mock server allows continue work on tests when API is not ready.

## Creating mock in Postman

1. Postman > Mock servers > Create mock server > Create new collection
2. request url > provide path e.g. `housholds/1/ownedBooks`
3. Provide mock server name
4. Mark checked: Save the mock server URL as environment variable
5. Create mock server
6. Collections > select your mock
7. Environment > select environment for mock
8. Send request. Observe response specified in mock settings.

## Creating additional mocked responses

1. Select response > click elipsis > add example
2. Update name and URL, e.g. `housheholds/2/ownedBooks`
3. Update RESPONSE body JSON:

```json
[
    {
        "id": 1,
        "titlel": "Don't Waste Your Life", 
        "author": "John Piper"
    }
]
```

4. Add header like `application/json` for `content-type`
5. Add response code

## Using mocked requests

1. Open collection
2. Ensure environment for mock is selected
3. Create GET `housheholds/2/ownedBooks`
4. Send request
5. Observe that response body and code 200 specified in mock are returned

## Mocking a feature

1. In mock collection create new request `{{url}}/households`
2. Add example with response
3. View environment variable
4. Copy url
5. Open browser `localhost:3000/mock` and paste copied url
6. Get response

## Return errors by mock server

1. Open  your mock server  collection
2. Open example and duplicate request `{{url}}/households/1/ownedBooks`
3. Rename to something like "Server error"
4. Delete response body
5. Change response code to `500`
6. Create nre request ot the same url `{{url}}/households/1/ownedBooks`
7. Add header `x-mock-response-code: 500`
8. Now send this request and observe 500 error response
9. Change url and send request  `{{url}}/households/2/ownedBooks` OR  `{{url}}/households/10/ownedBooks`
10. Observe 500 error response
11. Add header `x-mock-response-code:418`
12. Observe 404 error response "No matching requests"

## Postman matching algorithm for mock server examples

- matching
  - verb
  - URL: exact match, remove slashes, lowercase match, strip alpha-numeric
  - Response code (specified by header value)
- examples are scored
- does not match headers

## Creating documentation for collection

External consumers of API can benefit from documentation.

Required information

- URL
- Headers
- Request body
- Sample responses

Steps to view

1. Open Postman
2. Select collection
3. On the RHS click Documentation icon
4. Click View complete collection documentation

Add examples to documentation

1. Open request
2. 3 dots > Add example
3. Paste sample response into response body
4. Save it
5. Select folder or collection > View documentation
6. Observe documentation now has response example

Publish documentation

1. Postman > Open collection > View documentation
2. Upper right > Publish
3. Update settings as required
4. Click Publish
5. Copy URL and open in a browser the documentation page.
6. Click Run in Postman. This will allow users to run collection in Postman

## Team tools

Share collection

1. Open Postman
2. Select collection
3. 3 dots  > Share collection > Select Team Workspace
4. Alternatively can generate HTML code for button or public link to run in Postman
5. If anyone in the tea mwill delete or change request, it will be updated for other team members as well.

## Postman integrations

1. Open Postman
2. Click Home > Integrations > Browse all integrations
3. Find GitHub
4. Create new repository in GitHub
5. GitHub > click on user profile > Settings > developer settings > personal access token
6. Generate new token
7. Select "repo", "user" checkboxes
8. Paste token into Add integration page > access token > Authenticate and proceed
9. Select workspace, collection, select GitHub repository
10. Open GitHub repo and observe json file with collection data.

## Postman API

1. Open Postman
2. Click Home > Integrations > Browse all integrations
3. Find PostmanAPI
4. Observe Postman API collection opened
5. Select collection > Create a fork. This will allow to merge changes created in original repo
6. Open your workspace and select Postman API collection
7. Observe documentation on the RHS
8. Click `integrations dashboard` to generate API key
9. Generate and copy key
10. Add copied key in environment variable `postman_api_key`
11. Open `All collections` under Postman API and send request.
12. API allows change collections, environments, etc.

## Test examples: Lodash map()

Loop through items and return proiperty from each item

 ```js

 pm.sendRequest(getBooks, (err, books) => {
    const ids = _.map(books.json(),
        (book) => {
            return book.id;
        });
    pm.globals.set("bookIds", ids)
})

 
 ```

 Loop through a collection and return a deeply-nested property from each item

 ```js

 // Fetch the name of the first pet from each owner
var ownerArr = [{
    "owner": "Colin",
    "pets": [{"name":"dog1"}, {"name": "dog2"}]
}, {
    "owner": "John",
    "pets": [{"name":"dog3"}, {"name": "dog4"}]
}];

// Lodash
_.map(ownerArr, 'pets[0].name');
 
 ```

 ```js
 let responseData = pm.response.json();
 pm.test("Each item returned by location query for `Sydney` has `name` 'Sydney'", () => {
   _.each(responseData.data.locationQuery, (item) => {
    pm.expect(value.name).to.be.a('string').and.equal("Sydney");
    })
  });


```

## Lodash


```js 

var objA = {"name": "colin", "car": "suzuki", "age": 17};

var objB = objA.pick(['car', 'age']);
// {"car": "suzuki", "age": 17}

// Lodash
var objB = _.pick(objA, ['car', 'age']);
// {"car": "suzuki", "age": 17}

```

## Test examples: Lodash in pre-request script

```js
// Return random number between 0 and 1000 
_.random(1000);

// Return random number between 15 and 20 
_.random(15,20);

// Return random floating point number between 0 and 200 
_.random(20,true);



```

## Test examples: forEach

```js

responseValues.forEach((value) => {
    //console.log(`Value: ${value.assessment_se}`);
    pm.expect(value.assessment_se).to.be.a('number').and.is.within(0, 100);
    pm.expect(Number.isInteger(value.assessment_se)).to.be.true;
   
  });

```

```js
let responseData = pm.response.json();
pm.test("Each item returned by location query for `Sydney` has `name` 'Sydney'", () => {
    responseData.data.locationQuery.forEach((value) => {
        pm.expect(value.name).to.be.a('string').and.equal("Sydney");
        console.log(value.name)
    });
  });
```

Respones data

using the .map() function to get all the values from the ‘favourite_colour‘ property and placing those into separate arrays, then I’m using the .flatten() function to flatten the arrays into a single array. Finally, I’m using the _.uniq() function to filter the flattened array, to only return unique ‘favourite_colour’ values

```js

let colours = _.chain(pm.response.json())
.map('favourite_colours')
.flatten()
.uniq()
.value()
```

## Test example:  each section has 5 defined keys 

```js 

pm.test("Each section has 5 defined keys", () => {
    const responseValues = Object.values(jsonData);
    responseValues.forEach((value) => {
        pm.expect(value).to.have.all.keys("assessment_score", "assessment_se", "assessment_percentile", "version", "warnings")
    })
});

``` 

## Test example: Response has 7 sections

```js
pm.test("Response has 7 sections", () => {
    pm.expect(Object.keys(pm.response.json())).to.have.lengthOf(7);
});

```