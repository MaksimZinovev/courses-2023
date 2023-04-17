# postman fundamentals course pluralsight

## Links

- [Postman JavaScript reference | Postman Learning Center](https://learning.postman.com/docs/writing-scripts/script-references/postman-sandbox-api-reference/)
- [Scripting in Postman | Postman Learning Center](https://learning.postman.com/docs/writing-scripts/intro-to-scripts/)
- [Test script examples | Postman Learning Center](https://learning.postman.com/docs/writing-scripts/script-references/test-examples/#getting-started-with-tests)
- [Test script examples | Postman Learning Center](https://learning.postman.com/docs/writing-scripts/script-references/test-examples/#validating-response-structure)

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

## Using dynamic variables to geerate fake data

Example body demonstrating how to use dynamic variables to ganerate fake data

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

Add variable "host": "http://localhost:3000/users"

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



## Initializing test data 


Basic frlow 

1. Set up variables 
2. Create users 
3. Add books 
4. Clean up data

### 1. Set up variables 

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

## Loop over users 


Continue https://app.pluralsight.com/course-player?clipId=6c7b1abf-dd7b-46e3-bd0c-7e5e582850aa