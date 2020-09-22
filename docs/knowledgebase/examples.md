Die folgende Anfrage würde dieses *JSON* zurück geben: `https://api.forengoetter.org/knowledgebase?question=Ich+habe+einen+Merge+Fehler`
```
[tryit=https://api.forengoetter.org/knowledgebase?question=Ich+habe+einen+Merge+Fehler][/tryit]
[
    {   
        "id": 1,
        "link": "https:\/\/griefergames.de\/index.php?faq\/#entry-135",
        "text": "Alle wichtigen Informationen zum Mergen und wie man Merge-Bugs behebt, findest du im verlinkten FAQ-Artikel."
    }
]
```


Dies wäre eine Anfrage in welcher der `link` Parameter `null` sein könnte: `https://api.forengoetter.org/knowledgebase?question=Mein+Nachtbar+ist+Inaktiv`
```
[tryit=https://api.forengoetter.org/knowledgebase?question=Mein+Nachtbar+ist+Inaktiv][/tryit]
[
    {
        "id": 1,
        "link": null,
        "text": "Plots inaktiver Spieler lassen sich derzeit nicht mehr \u00fcber das Forum beantragen. Du kannst dies aktuell nur als Wunsch bei einem Admin \u00e4u\u00dfern."
    }
]
```
