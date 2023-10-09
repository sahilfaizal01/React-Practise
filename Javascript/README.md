# Javascript Review
## DESTRUCTURING OF ARRAYS AND OBJECTS
```
const book = getBook(2);
book;

const { title, author, pages, publicationDate, genres, hasMovieAdaptation } = book;

console.log(author, title);

// accessing first two elements of genres array
const [primaryGenre, secondaryGenre] = genres;
console.log(primaryGenre, secondaryGenre);
```
## REST AND SPREAD OPERATOR
```
// REST- we can only place this at end
const [primaryGenre, secondaryGenre, ...otherGenres] = genres;
console.log(primaryGenre, secondaryGenre, otherGenres); //otherGenres will be an array containing the other elements of the genres array

// SPREAD- take all the elements out and spread them one by one
const newGenres = [...genres, "epic fantasy"]; //adding a new element to the genres array
newGenres;
// Adding new properties or updating existing ones to objects
const updatedBook = {
  ...book,
  moviePublicationDate: "2001-12-19",
  pages: 1400,
};
updatedBook;
```
## TEMPLATE LITERALS
```
const summary = `${title} is a book with ${pages} pages, was written by ${author} and published in ${
  publicationDate.split("-")[0]
}. The book has ${hasMovieAdaptation ? "" : "not"} been adapted as a movie`;
summary;
```

## TERNARY OPERATORS
```
const pagesRange = pages > 1000 ? "over a thousand" : "less than 1000";
pagesRange;
console.log(`The book has ${pagesRange} pages`);
```
## ARROW FUNCTIONS
```
const getYear = (str) => str.split("-")[0];
console.log(getYear(publicationDate));
```
## SHORT CIRCUITING
### <ins>&& Operator</ins>
#### true and true -> returns second value
#### false and true -> return first value
```
console.log(true && "some string");
console.log(false && "some string");
console.log(hasMovieAdaptation && "this book has a movie");
console.log("jonas" && "some string");
console.log(0 && "some string");
```
### <ins>|| Operator</ins>
#### true and true -> returns first value
#### false and true -> returns second value
```
console.log(true || "some string");
console.log(false || "some string");
```
### <ins>?? Operator</ins>
```
const spanishTranslation = book.translations.spanish || "NOT TRANSLATED";
spanishTranslation; // NOT TRANSLATED

console.log(book.reviews.librarything.reviewsCount); // 0
const countWrong = book.reviews.librarything.reviewsCount || "no data";
countWrong; // no data

const count = book.reviews.librarything.reviewsCount ?? "no data";
count; // 0
```
## OPTIMAL CHAINING OPERATOR
```
function getTotalReviewCount(book) {
    const goodreads = book.reviews?.goodreads?.reviewsCount ?? 0;
    const librarything = book.reviews?.librarything?.reviewsCount ?? 0;
    return goodreads + librarything;
}

console.log(getTotalReviewCount(book));
```
