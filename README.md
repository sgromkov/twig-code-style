# twig-code-style-extended
An extended twig code style guide

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
{#comment }
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
