## Pluggin pour les créer des pages à partir de CSV



https://github.com/avillafiorita/jekyll-datapage_gen



**Dans config.yml**

→ ajouter le plugin à la liste des plugins

```
plugins:
  - jekyll-datapage-generator
```

→ Configurer le plugin:

```yml
page_gen:
- data: data-efa
  template: fiche
  dir: fiches
  index_files: false
  name: identifiant
  #name_expr: [a Ruby expression to generate the filename (alternative to name)]
  title: titre
  #title_expr: [a Ruby expression to generate the filename (alternative to title)]
  extension: .html
  #filter: [property to filter data records by]
  #filter_condition: [a Ruby expression to filter data]
  #page_data_prefix: [prefix used to name variables]
  #debug: [boolean, if true output more informative messages]
```





**Dans Gemfile**



→ ajouter aussi le pluggin, (trouver le group de pluggin s'il existe déjà):

```
group :jekyll_plugins do
  # gem "jekyll-feed", "~> 0.12"
  gem "jekyll-datapage-generator"
end
```

→ ne pas oublier de faire `bundle install`





## Créer un layout pour chaque fiche (fiche.html dans `_layouts`)

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>

    <article id="{{ page.identifiant }}">
        <h1>{{ page.titre }}</h1>
        <p>{{ page.type }}</p>
    </article>
</body>
```



## Incrementer tous les items dans une seule page à partir dùn layout (chapitre.html)

```html
 <section id="fiches">
      <ul>
          {% for item in site.data.data-efa %}
            <li id="{{ item.identifiant }}">
                {{ item.titre }}
                {{ item.type }}
            </li>
          {% endfor %}
          </ul>
  </section>
```

