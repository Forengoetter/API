#### Typ *list*

| Rückgabename      | Beschreibung                                                            |
| ----------------- | ----------------------------------------------------------------------- |
| id                | ID des Blogs.                                                           |
| userID            | Die ID des Benutzers welcher diesen Blog verölffentlicht hat.           |
| username          | Der Benutzername des Benutzers welcher diesen Blog verölffentlicht hat. |
| time              | UNIX Zeit der Veröffentlichung des Blogs.                               |
| categoryID        | Die ID der Kategorie in welcher dieser Blog verölffentlicht wurde.      |
| views             | Ansichten dieses Blogs.                                                 |
| title             | Titel des Blogs.                                                        |
| teaser            | Teasertext des Blogs.                                                   |

#### Typ *entry*

Der Parameter *id* muss gesetzt sein.

| Rückgabename      | Beschreibung                                |
| ----------------- | ------------------------------------------- |
| id                | ID des Blogs.                               |
| title             | Titel des Blogs.                            |
| teaser            | Teasertext des Blogs.                       |
| content           | Inhalt des Blogs, dieser enthält HTML.      |
| image             | Bild des Blogs, kann auch null sein.        |
| teaserImage       | Teaserbild des Blogs, kann auch null sein.  |
