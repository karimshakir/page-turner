# vuejs-booksearch

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

DESCRIPTION

This application allows you to use the Google Books API to search for books.

This application allows you to:
Type in a query and display a list of books matching that query.
Each item in the list includes the book's author, title, and publishing company, as well as a picture of the book.
Finally, from each list item, you should can navigate to more information about the book, via a link out to an 
external site with more information about that particular book.

It has a custom background, and minor styling.  

APPROACH

My approach to building this application was to first create a MVP (skeleton) project that accomplishes the 
user stories and requirements.  
Next I use the application and compare it to the user story and existing Google Books application to observe features,
functionality and identify edge cases. I test for these cases, and systematically solve them. 

Afterwards I add some styling and in able to view page with ease.

ISSUES

Some of the issues I encountered included incorporating the thumbnail, as well as the More Info link.  
At time to submission, I was working on adding more "happ/sad paths" for blank as well as queries that return no data.
Finally I wanted to add more styling that better resembles google.books.  


