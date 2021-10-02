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

Write project.app py according to tutorial.
```python3
from flask import Flask # Import Flask web framework

# init flask application
app = Flask(__name__)

# Add root url route
@app.route("/")
def hello():
    return "Hello, World!" # Return hello world from root URL

# Run the Flask application
if __name__ == "__main__":
    app.run()
```

Write tests/app_test.py accordint to tutorial.
```
from project.app import app

# Index test
def test_index():
    tester = app.test_client()
    response = tester.get("/", content_type="html/text") # Get root url
 
    # Check that we get status code 200 back
    assert response.status_code == 200 # 
    # Check that the result is "Hello, World"
    assert response.data == b"Hello, World!"
```

Getting issue with obsolete json from Flask

```python3
env/lib/python3.7/site-packages/flask/json/__init__.py:103
  /home/chris/src/python/flaskr-tdd/env/lib/python3.7/site-packages/flask/json/__init__.py:103: DeprecationWarning: Importing 'itsdangerous.json' is deprecated and will be removed in ItsDangerous 2.1. Use Python's 'json' module instead.
    class JSONDecoder(_json.JSONDecoder):

-- Docs: https://docs.pytest.org/en/stable/warnings.html
================================ 1 passed, 3 warnings in 0.09s =================================
```

Fixing issue by upgrading Flask and Pytest
```bash
pip install pytest
pip install flask
```

Getting passing Python unit tests
```python3
python -m pytest
===================================== test session starts ======================================
platform linux -- Python 3.7.3, pytest-6.2.5, py-1.10.0, pluggy-0.13.1
rootdir: /home/chris/src/python/flaskr-tdd
collected 1 item                                                                               

tests/app_test.py .                                                                      [100%]

====================================== 1 passed in 0.09s =======================================
```