---
title: Selenium
---

## Links
- [Selenium doc](https://www.selenium.dev/documentation/)
- [Selenium with Python](https://selenium-python.readthedocs.io/)
- [Webdriver Manager for Python](https://github.com/SergeyPirogov/webdriver_manager)

## Options and commands
- implicit wait
  - tells WebDriver to poll DOM for a certain amount of time when trying to find any element
  - `driver.implicitly_wait(10)`
  - also see [Implicit Waits](https://selenium-python.readthedocs.io/waits.html#implicit-waits)

## Examples
#### Minimal:
```python
from selenium import webdriver
driver = webdriver.Chrome()
driver.get("http://selenium.dev")
print(driver.title)
driver.quit()
```

#### Minimal headless:
```python
from selenium import webdriver
from selenium.webdriver import ChromeOptions
options = ChromeOptions()
options.add_argument("--headless=new")
driver = webdriver.Chrome(options=options)
driver.get("http://selenium.dev")
print(driver.title)
```
