YAML unterstützt verschiedene Datentypen, die man aus anderen Sprachen auch so kennt.

## Strings (Zeichenketten), '' oder ""

```YAML
info:
  version: '1.2'
  other_version: "1.9"
```

## Booleans (yamllint kennt nur "true" bzw. "false")

```YAML
create_key: true
needs_agent: false
knows_oop: True
likes_emacs: False
likes_me: TRUE
uses_cvs: FALSE
```

## Listen

```YAML
fruits:
  - Apple
  - Orange
  - Strawberry
  - Mango

// Oder in Kurzform
fruits: ['Apple', 'Orange', 'Strawberry', 'Mango']
```

## Dictionaries

```YAML
martin:
  name: Martin D'vloper
  job: Developer
  skill: Elite

// Oder in Kurzform
martin: {name: Martin D'vloper, job: Developer, skill: Elite}
```

## Listen von Dictionaries
```YAML
# Employee records
employees:
  - martin:
      name: Martin D'vloper
      job: Developer
      skills:
        - python
        - perl
        - pascal
  - tabitha:
      name: Tabitha Bitumen
      job: Developer
      skills:
        - lisp
        - fortran
        - erlang
```

## Referenzen
[Ansible Docs](https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html)