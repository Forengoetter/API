# Instructions
In this file you will find the instructions for handling the api docs

1. create a folder in the `docs` folder (use a good name because it's associated with the namespace)
2. go into this created folder and create a file named `config.json`, without this file the system won't recognize that there is any content
2.1. open the `config.json` file and put in the **JSON** content (I'll use numbers associated with the descriptions below):
```json
{
    "title" : "1",
    "icon" : "2",
    "description" : "3",
    "keywords" : [
        "4"
    ],
    "page" : "5",
    "pages" : [
        {
            "title" : "6",
            "page" : "7"
        }
    ]
}
```
1) the title of this api, "Blogs" for example
2) any html tag that should be used as icon, for security reasons only `img` and `i` Tags are allowed (`i` Tags only in combination with a fontawensone class). A simple icon        could look like this: `<i class='fas fa-rss'></i>` (we have Fontawensome v5.13.0 installed)
3) a short description of this api
4) an endless number of keywords (in the json array), used for the search system
5) the markdown string or the filename of the *index* file (only files in the directory of the config file are allowed to be used!)
6) this is an object in the pages array, in this case its the title
7) the markdown string or the filename of the file used for this page (only files in the directory of the config file are allowed to be used!)

In all markdown cases you can use GFM, you also can use two custom *BB-Codes*, both should only be used within code blocks:
- [tryit={URL}][/tryit] => creates an **TryIt** Button for the given URL
- [author={AUTHOR}] => adds an simple author note on a pice of code

