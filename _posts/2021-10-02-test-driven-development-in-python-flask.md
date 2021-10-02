---
layout: post
title: Test driven development in Python Flask
date: 2021-10-02T11:58:10.518Z
thumbnail: https://upload.wikimedia.org/wikipedia/commons/thumb/3/3c/Flask_logo.svg/96px-Flask_logo.svg.png
---
Following the tutorial on

<https://github.com/mjhea0/flaskr-tdd#project-setup>

This is notes following mjhea0 tutorial

`mkdir flaskr-tdd`

`cd flaskr-tdd`

Create Python environment

`python3 -m venv env`

`env/bin/activate`

Install flask Python minimal web framework

`pip install flask==1.1.2`

Install PyTest testing framework

`pip install pytest==6.1.1`

Create project skeleton structure

```bash
mkdir project
mkdir tests
touch project/__init__.py
touch project/app.py
touch tests/__init__.py
touch tests/app_test.py
```