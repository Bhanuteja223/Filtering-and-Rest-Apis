## REST APIs
- Get Books API
  - Filtering books
  Example:
    --> Get a specific number of books
    --> Get books based on search query text
    --> Get books in sorted order


  ** To get specific number of books in certain range, We use "limit and offset"

  offset: offset is used to specify the "position" from where rows to be selected.
  Limit: limit is used to specify the "number of rows".

  Ex: 
  "http://localhost:3000/books/?limit=3"
  "http://localhost:3000/books/?offset=2&limit=3"
  "http://localhost:3000/author/20/books/?offset=2"

  Accesing Query Parameters:
  Query Parameters are sorted inside a request.query object in the form of key value pairs.
                    {
  request.query ==>   offset: '2',
                      limit: '3'                     
                    }

  --> Get books based on search query text: search_q = "potter"
  --> Get books in sorted order: ASC or DESC

  Now overall URL looks like:
       http://....?limit=15&offset=5&search_q=potter&order_by=price&order=DESC
                      
   
HTTP Response:

"Method": "GET" 
"Status-Code": "200 - OK" 
"content-length": "1127"
"content-type": "application/json; charset=utf-8"
 

[
    {
        "book_id": 4,
        "title": "Harry Potter and the Chamber of Secrets",
        "author_id": 1,
        "rating": 4.43,
        "rating_count": 2889372,
        "review_count": 56139,
        "description": "Ever since Harry Potter had come home for the summer.",
        "pages": 341,
        "date_of_publication": "June 2nd 1999",
        "edition_language": "English",
        "price": 850,
        "online_stores": "Amazon, Audible,Google play, Indigo,Abebooks"
    },
    {
        "book_id": 2,
        "title": "Harry Potter and the Deathly Hallows",
        "author_id": 1,
        "rating": 4.62,
        "rating_count": 2944470,
        "review_count": 68081,
        "description": "Harry Potter is leaving Privet Drive for the last time.",
        "pages": 759,
        "date_of_publication": "July 21st 2007",
        "edition_language": "English",
        "price": 800,
        "online_stores": "Amazon, Audible,Google play, Indigo,Abebooks"
    },
    {
        "book_id": 1,
        "title": "Harry Potter and the Sorcerers Stone",
        "author_id": 1,
        "rating": 4.48,
        "rating_count": 7464819,
        "review_count": 118312,
        "description": "Harry Potters life is miserable. His parents are dead and hes stuck with his heartless relatives.",
        "pages": 309,
        "date_of_publication": "November 1st 2003",
        "edition_language": "English",
        "price": 750,
        "online_stores": "Amazon, Audible,Google play, Indigo,Abebooks"
    }
]

We can give default values during destructuring assignment. It works if variable doesn't exist or if value is undefined.

Ex: const {offset, limit, order_by, order, search_q = " "} = request.query
search_q = " " is a default value;

Note: If there are more query Parameters, use the POST method insted of the GET method and pass them in the request body.

- Rest APIs
[REST] - Representational State Transfer.

  - What are REST APIs?
        REST is a "set of Principles" that define how
        Web standards, such as HTTP and URLs, 
        are supposed to be used.

  - REST Principles
   1. Each and every book has its own "unique id"
   which helps to identify and access it.
   2. Using standard methods: These "standard methods"
   defining in the HTTP specifications with guaranteed behaviour.
   3. Accept and Respond with JSON

===> Using REST Principles improves the application in various 
aspects like "scalability, reliability, etc...."
