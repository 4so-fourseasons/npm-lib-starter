[![Build Status](https://travis-ci.org/{{cookiecutter.namespace}}/{{cookiecutter.project_name}}.svg?branch=master)](https://travis-ci.org/{{cookiecutter.namespace}}/{{cookiecutter.project_name}})
[![Coverage Status](https://coveralls.io/repos/github/{{cookiecutter.namespace}}/{{cookiecutter.project_name}}/badge.svg?branch=master)](https://coveralls.io/github/{{cookiecutter.namespace}}/{{cookiecutter.project_name}}?branch=master)
[![npm version](https://badge.fury.io/js/{%- if cookiecutter.scoped_package == 'yes' -%}%40{{cookiecutter.namespace}}%2F{%- endif -%}{{cookiecutter.project_name}}.svg)](https://badge.fury.io/js/{%- if cookiecutter.scoped_package == 'yes' -%}%40{{cookiecutter.namespace}}%2F{%- endif -%}{{cookiecutter.project_name}})
[![api docs](https://img.shields.io/badge/docs-API-C8022F.svg)](https://{{cookiecutter.namespace}}.github.io/{{cookiecutter.project_name}})

[![JavaScript Style Guide](https://cdn.rawgit.com/standard/standard/master/badge.svg)](https://github.com/standard/standard)

# {{cookiecutter.project_name}}

{{cookiecutter.short_description}}


## Installation

```shell
npm i --save {% if cookiecutter.scoped_package == 'yes' %}@{{cookiecutter.namespace}}/{% endif %}{{cookiecutter.project_name}}
```


## Usage

## Documentation

[API](https://{{cookiecutter.namespace}}.github.io/{{cookiecutter.project_name}})

[GitHub](https://github.com/{{cookiecutter.namespace}}/{{cookiecutter.project_name}})

## Versioning

We use [SemVer](http://semver.org/) for versioning.
