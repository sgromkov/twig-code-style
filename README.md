# Twig code style. Extended

An extended twig code style guide. Based on [the official Coding Standarts](https://twig.symfony.com/doc/2.x/coding_standards.html) and extended with ❤️ by Sergey Gromkov.

The current style guide contains all the rules of [the official guide](https://twig.symfony.com/doc/2.x/coding_standards.html), and additional rules I implemented working in [matchtv.ru](https://matchtv.ru).

## Horizontal spaces

### Spaces inside operators

Put one (and only one) space:
- after the start of a delimiter `{{`, `{%`, and `{#`
- before the end of a delimiter `}}`, `%}`, and `#}`

```twig
✅ good

{{ foo }}
{# comment #}
{% if foo %}{% endif %}  
```


```twig
❌ bad

{{foo}}
{#comment#}
{%if foo%}{%endif%}  
```

When using the whitespace control character, do not put any spaces between it and the delimiter:

```twig
✅ good

{{- foo -}}
{#- comment -#}
{%- if foo -%}{%- endif -%}
```

```twig
❌ bad

{{-foo-}}
{#-comment-#}
{%-if foo-%}{%-endif-%}
```

Put one (and only one) space before and after the following operators:
- comparison operators: `==`, `!=`, `<`, `>`, `>=`, `<=`
- math operators: `+`, `-`, `/`, `*`, `%`, `//`, `**`
- logic operators: `not`, `and`, `or`
- `~`, `is`, `in`, and the ternary operator `?:`

```twig
✅ good

{{ 1 + 2 }}
{{ foo ~ bar }}
{{ true ? true : false }}
```

```twig
❌ bad

{{ 1+2 }}
{{ foo~bar }}
{{ true ? true:false }}
```

Put one (and only one) space after the `:` sign in hashes and `,` in arrays and hashes:

```twig
✅ good

{{ [1, 2, 3] }}
{{ {'foo': 'bar'} }}
```

```twig
❌ bad

{{ [1,2,3] }}
{{ {'foo':'bar'} }}
```

Do not put any spaces after an opening parenthesis and before a closing parenthesis in expressions:
```twig
✅ good

{{ 1 + (2 * 3) }}
```

```twig
❌ bad

{{ 1+(2*3) }}
```

Do not put any spaces before and after string delimiters:

```twig
✅ good

{{ 'foo' }}
{{ "foo" }}
```

```twig
❌ bad

{{'foo'}}
{{" foo "}}
```

Do not put any spaces before and after the following operators: `|`, `.`, `..`, `[]`:

```twig
✅ good

{{ foo|upper|lower }}
{{ user.name }}
{{ user[name] }}
{% for i in 1..12 %}{% endfor %}
```

```twig
❌ bad

{{ foo | upper | lower }}
{{ user . name }}
{{ user[ name ] }}
{% for i in 1 .. 12 %}{% endfor %}
```

Do not put any spaces before and after the parenthesis used for filter and function calls:

```twig
✅ good

{{ foo|default('foo') }}
{{ range(1..10) }}
```

```twig
❌ bad

{{ foo | default('foo') }}
{{ foo|default ('foo') }}
{{ range (1..10) }}
```

Do not put any spaces before and after the opening and the closing of arrays and hashes:

```twig
✅ good

{{ [1, 2, 3] }}
{{ {'foo': 'bar'} }}
```

```twig
❌ bad

{{ [ 1, 2, 3 ] }}
{{ { 'foo': 'bar' } }}
```

### Indents inside blocks

Indent your code inside tags (use the same indentation as the one used for the target language of the rendered template):

```twig
✅ good

{% block foo %}
    {% if true %}
        true
    {% endif %}
{% endblock %}
```

```twig
❌ bad

{% block foo %}
{% if true %}
    true
{% endif %}
{% endblock %}
```

### Indents in comments

Comments that span one line will have the comment indicators on the same line as the comment:

```twig
✅ good

<div class="image-widget-data">
  {# Render widget data without the image preview that was output already. #}
  {{ data|without('preview') }}
</div>
```

```twig
❌ bad

<div class="image-widget-data">
  {# 
    Render widget data without the image preview that was output already. 
  #}
  {{ data|without('preview') }}
</div>
```

Comments that span more than one line will have the comment indicators on separate lines. Comments should be wrapped so the line is less than 80 characters:

```twig
✅ good

{#
  This is a very long comment. It spans more than one line. This is a very
  long comment. It spans more than one line. This is a very long comment. It
  spans more than one line. This is a very long comment. It spans more than
  one line. 
#}
<div class="{{ attributes.class }}"{{ attributes }}>
  {{ content }}
</div>
```

```twig
❌ bad

{#
  This is a very long comment. It spans more than one line. This is a very long comment. It spans more than one line. This is a very long comment. It spans more than one line. This is a very long comment. It spans more than one line. 
#}
<div class="{{ attributes.class }}"{{ attributes }}>
  {{ content }}
</div>
```

## Vertical spaces

### Spaces between operations

Put an empty line between imports and variables:

```twig
✅ good

{% macro match(props) %}
    {% from 'site/macros/club/index.html.twig' import club %}

    {% set group_name = props.group_name|default('') %}
    {% set teams = props.teams|default([]) %}
    ...
{% endmacro %}
```

```twig
❌ bad

{% macro match(props) %}
    {% from 'site/macros/club/index.html.twig' import club %}
    {% set group_name = props.group_name|default('') %}
    {% set teams = props.teams|default([]) %}
    ...
{% endmacro %}
```

### Spaces after the macro definition

Do not put an empty line between the macro name and its contents:

```twig
✅ good

{% macro match(props) %}
    {% from 'site/macros/club/index.html.twig' import club %}
    ...
{% endmacro %}
```

```twig
❌ bad

{% macro match(props) %}

    {% from 'site/macros/club/index.html.twig' import club %}
    ...
{% endmacro %}
```

```twig
✅ good

{% macro match(props) %}
    {% set group_name = props.group_name|default('') %}
    {% set teams = props.teams|default([]) %}
    ...
{% endmacro %}
```

```twig
❌ bad

{% macro match(props) %}

    {% set group_name = props.group_name|default('') %}
    {% set teams = props.teams|default([]) %}
    ...
{% endmacro %}
```

```twig
✅ good

{% macro match(props) %}
    <div class="match">
        ...
    </div>
{% endmacro %}
```

```twig
❌ bad

{% macro match(props) %}

    <div class="match">
        ...
    </div>
{% endmacro %}
```

Do not put an empty line between the closing construction of the macro and its contents:

```twig
✅ good

{% macro match(props) %}
    <div class="match">
        ...
    </div>
{% endmacro %}
```

```twig
❌ bad

{% macro match(props) %}
    <div class="match">
        ...
    </div>

{% endmacro %}
```

### An empty line at the end of the file

Add an empty line at the end of the file. Configure your editor to do this automatically.

## Naming

### Naming variables

Use lower cased and underscored variable names:

```twig
✅ good

{% set foo = 'foo' %}
{% set foo_bar = 'foo' %}
```

```twig
❌ bad

{% set Foo = 'foo' %}
{% set fooBar = 'foo' %}
```

### Naming macros

The same macro should be named the same in all its templates:

```twig
✅ good

{# templates/site/macros/match/index.html.twig #}

{% macro match(props) %}
    ...
{% endmacro %}
```

```twig
✅ good

{# templates/site/macros/match/reversed.html.twig #}

{% macro match(props) %}
    ...
{% endmacro %}
```


```twig
✅ good

{# templates/site/macros/match/standings.html.twig #}

{% macro match(props) %}
    ...
{% endmacro %}
```

```twig
❌ bad

{# templates/site/macros/match/index.html.twig #}

{% macro default_match(props) %}
    ...
{% endmacro %}
```

```twig
❌ bad

{# templates/site/macros/match/reversed.html.twig #}

{% macro reversed_match(props) %}
    ...
{% endmacro %}
```

```twig
❌ bad

{# templates/site/macros/match/standings.html.twig #}

{% macro match_standings(props) %}
    ...
{% endmacro %}
```

### Naming files

All macros, components, embeds, etc. should be in their own folders:

```twig
✅ good

📂 templates
└── 📂 site
    ├── 📂 macros
    |   ├── 📂 match
    |   |   ├── index.html.twig
    |   |   ├── reversed.html.twig
    |   |   └── standings.html.twig
    |   ├── 📂 club
    |   |   └── index.html.twig
    |   └── 📂 menu
    |       └── index.html.twig
    ├── 📂 embeds
    |   └── 📂 content_section
    |       └── index.html.twig
    └── 📂 components
        └── 📂 footer
            └── index.html.twig
```

```twig
❌ bad

📂 templates
└── 📂 site
    ├── 📂 macros
    |   ├── match.html.twig
    |   ├── match_reversed.html.twig
    |   ├── match_standings.html.twig
    |   ├── club.html.twig
    |   └── menu.html.twig
    ├── 📂 embeds
    |   └── content_section.html.twig
    └── 📂 components
        └── footer.html.twig
```

## Incoming Parameters

### Description of incoming parameters

A docblock at the top of a Twig template should be wrapped in the twig comment markers, `{#` and `#}`:

```twig
✅ good

{#
 # @param string loader_url
 #     The url to request the content.
 #     If not specified, content will not be requested.
 #
 # @param string loader_type
 #     A type of loading listener.
 #     Could be one of: 'BASIC', 'SCROLL', 'BUTTON'.
 #     Default: 'BASIC' (2 scrolls, than button).
 #
 # @param boolean loader_is_active
 #     Defines whether to launch loading listeners (loader_type),
 #     and request the content (loader_url).
 #     If not specified, content will not be requested.
 #
 # @param string loader_subscriber
 #     Event type name to subscribe for PubSub's messages.
 #     If not specified, will not subscribe for messages.
 #
 # @param object loader_params
 #     Initial params consistent to initial content.
 #     If not specified, will not participate in the first url generation.
 #
 # @param boolean loader_updated_addressbar_url
 #     Defines whether to update address bar url,
 #     when the url was requested.
 #
 # @param boolean use_default_container
 #     Defines whether to create a wrapper around the content.
 #     This wrapper is used for inserting the requested content.
 #     If not specified, wrapper will not be created,
 #     and developer should insert the wrapper itself in the content.
 #
 # @param string error
 #     Alternative error message.
 #     If not specified, the default message will be used.
 #}
```

### Using `|default` in incoming parameters

`|default` should be set only to those properties without which the macro can work. If the task of the macro is to show the headline of the news, then `|default` should not be applied to the headline.

The same goes for the news list. If the task of the macro is to display a list of news, then you do not need to do `news|default([])` , and you do not need to check for the presence of transmitted news in the macro. We should expect that the macro will either output a list, or throw an error that there is no data.

Checking for the presence of data should be at a higher level, in the parent. This is most often in the view components of the page, if a macro is called directly in them.

The main idea is that we should be able to get errors from twig if we haven't passed something very important to macros. This way we will be able to react quickly, thanks to Sentry and logs, and fix it. The most recent example where we paid for it was the video tab in the club: we messed up with incoming data during refactoring, and due to the fact that everything was covered with defaults, the macros simply didn't output anything, and we got an empty page that we hadn't noticed for several weeks. Although it would be correct to get the error of missing data on the first day after the deployment and fix it quickly.

```twig
✅ good

{% set nodes = props.nodes %}

{% for node in nodes %}
    ...
{% endfor %}
```

```twig
❌ bad

{% set thumbs = props.thumbs|default([]) %}

{% if thumbs is iterable and thumbs|length %}
    ...
{% endif %}
```

Protection against the absence of important data should be done at the level of views, which already cause macros inside themselves. That is, the macros themselves are not protected in any way - their task is to output either a layout or an error. But in the views we are already checking whether there is data, and based on this we make a decision to output something or not.
