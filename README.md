# Json2HTML

Json tree converter into an HTML table heavily inspired by the python **[json2html · PyPI](https://pypi.org/project/json2html)** library.

## Examples

###### Example 1: Base usage

input:

```json
input = {
 "name": "json2html",
 "description": "Converts JSON to HTML tabular representation"
}
```

```php
Json2Html::convert($input);
```

output:

```html
<table>
    <thead>
        <tr>
            <th>name</th>
            <th>description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>json2html</td>
            <td>converts JSON to HTML tabular representation</td>
        </tr>
    </tbody>
</table>
```

<table><thead><tr><th>name</th><th>description</th></tr></thead><tbody><tr><td>json2html</td><td>converts JSON to HTML tabular representation</td></tr></tbody></table>

###### Example 2: Setting custom attributes to table

input:

```json
input = {
 "name": "json2html",
 "description": "Converts JSON to HTML tabular representation"
}
```

```php
Json2Html::id('info-table')
    ->class('table table-bordered table-hover')
    ->convert($input);

Json2Html::id('info-table')
    ->class(['table', 'table-bordered', 'table-hover'])
    ->convert($input);

Json2Html::id('info-table')
    ->class('table')
    ->class('table-bordered')
    ->class('table-hover')
    ->convert($input);
```

output:

```html
<table id="info-table" class="table table-bordered table-hover">
    <thead>
        <tr>
            <th>name</th>
            <th>description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>json2html</td>
            <td>converts JSON to HTML tabular representation</td>
        </tr>
    </tbody>
</table>
```

<table id="info-table" class="table table-bordered table-hover"><thead><tr><th>name</th><th>description</th></tr></thead><tbody><tr><td>json2html</td><td>converts JSON to HTML tabular representation</td></tr></tbody></table>

###### Exemple 3:

input:

```json
input = {
 "name": "json2html",
 "description": "Converts JSON to HTML tabular representation"
}
```

```php
Json2Html::header('Nome', 'Descrição')
    ->convert($input);

Json2Html::header(['Nome', 'Descrição'])
    ->convert($input);

Json2Html::header('Nome')
    ->header('Descrição')
    ->convert($input);
```
```html
<table>
    <thead>
        <tr>
            <th>Nome</th>
            <th>Descrição</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>json2html</td>
            <td>converts JSON to HTML tabular representation</td>
        </tr>
    </tbody>
</table>
```


###### Exemple 3:

input:

```json
input = {
 "languages": [{"language": "PHP"}, {"language": "JS"}, {"language": "CSS"}],
 "databases": [{"database": "Postgres"}, {"database": "MySQL"}, {"database": "SQLite"}]
}
```

```php
Json2Html::header(['Linguagens', 'Banco de dados', ['Linguagem', 'Banco']])
    ->convert($input);


Json2Html::header(['Linguagens', ['Linguagem']])
    ->header(['Banco de dados', ['Banco']])
    ->convert($input);
```
```html
<table>
    <thead>
        <tr>
            <th>Linguagens</th>
            <th>Banco de dados</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>
                <table>
                    <thead>
                        <tr>
                            <th>Linguagem</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>PHP</td>
                            <td>JS</td>
                            <td>CSS</td>
                        </tr>
                    </tbody>
                </table>
            </td>
            <td>
                <table>
                    <thead>
                        <tr>
                            <th>Banco</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>Postgres</td>
                            <td>MySQL</td>
                            <td>SQLite</td>
                        </tr>
                    </tbody>
                </table>
            </td>
        </tr>
    </tbody>
</table>
```



###### **Example 5:** Clubbing same keys of: Array of Objects

input:

```json
input = {
        "sample": [{
                "a":1, "b":2, "c":3
        }, {
                "a":5, "b":6, "c":7
        }]
}
```

```php
Json2Html::convert($input);
```

output:

```html
<table>
    <thead>
        <tr>
            <th>sample</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>
                <table>
                    <thead>
                        <tr>
                            <th>b</th>
                            <th>c</th>
                            <th>a</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>2</td>
                            <td>3</td>
                            <td>1</td>
                        </tr>
                        <tr>
                            <td>6</td>
                            <td>7</td>
                            <td>5</td>
                        </tr>
                    </tbody>
                </table>
            </td>
        </tr>
    </tbody>
</table>
```
