# R-cheat-sheet

## General
* [import and tidy data](https://github.com/jananiravi/cheatsheets/blob/master/r/tidyverse-data-import-cheatsheet.pdfhttps://github.com/jananiravi/cheatsheets/blob/master/r/tidyverse-data-import-cheatsheet.pdf)

## Week 1

## Week 2

## Week 3

## Week 4

### tidyverse
* filter data
* mutate a variable (into a new variable)
* sort data
* *and don't forget to use the pipe again after every line*
```
gapminder %>%
    filter(year == 2007) %>%
    mutate(lifeExpMonths = 12 * lifeExp) %>%
    arrange(desc(lifeExpMonths))
```

## How to use this format:

* writing a list
* is like this

## This is the second title

1. haha
2. hehe
3. hihi

```
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```

| Syntax | Description |
| ----------- | ----------- |
| Header | Title |
| Paragraph | Text |

[title](https://www.example.com)
  
- [x] Write the press release
- [ ] Update the website
- [ ] Contact the media

~~The world is flat.~~

**bold text**

*italicized text*

==highlight==

<mark>highlight</mark>
