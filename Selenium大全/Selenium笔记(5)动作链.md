# Selenium笔记（5）动作链

本文集链接：https://www.jianshu.com/nb/25338984 



## 简介

一般来说我们与页面的交互可以使用`Webelement`的方法来进行点击等操作。但是，有时候我们需要一些更复杂的动作，类似于拖动，双击，长按等等。

这时候就需要用到我们的`Action Chains`（动作链）了。



## 简例

```python
from selenium.webdriver import ActionChains

element = driver.find_element_by_name("source")
target = driver.find_element_by_name("target")

actions = ActionChains(driver)
actions.drag_and_drop(element, target)
actions.perform()
```

在导入动作链模块以后，需要声明一个动作链对象，在声明时将webdriver当作参数传入，并将对象赋值给一个actions变量。

然后我们通过这个actions变量，调用其内部附带的各种动作方法进行操作。

**注：在调用各种动作方法后，这些方法并不会马上执行，而是会按你代码的顺序存储在ActionChains对象的队列中。当你调用perform()时，这些动作才会依次开始执行。**



## 常用动作方法

- `click`(*on_element=None*) 

  左键单击传入的元素，如果不传入的话，点击鼠标当前位置。

- `context_click`(*on_element=None*) 

  右键单击。

- `double_click`(*on_element=None*) 

  双击。

- `click_and_hold`(*on_element=None*)

  点击并抓起

- `drag_and_drop`(*source*, *target*) 

  在source元素上点击抓起，移动到target元素上松开放下。

- `drag_and_drop_by_offset`(*source*, *xoffset*, *yoffset*) 

  在source元素上点击抓起，移动到相对于source元素偏移xoffset和yoffset的坐标位置放下。

- `send_keys`(**keys_to_send*) 

  将键发送到当前聚焦的元素。

- `send_keys_to_element`(*element*, **keys_to_send*) 

  将键发送到指定的元素。

- `reset_actions`() 

  清除已经存储的动作。



## 完整文档

*class* `selenium.webdriver.common.action_chains.``ActionChains`(*driver*) 

Bases: `object` 

ActionChains are a way to automate low level interactions such as mouse movements, 	mouse button actions, key press, and context menu interactions. This is useful for doing more complex actions like hover over and drag and drop. 

Generate user actions.

When you call methods for actions on the ActionChains object, the actions are stored in a queue in the ActionChains object. When you call perform(), the events are fired in the order they are queued up.

ActionChains can be used in a chain pattern: 

```python
menu = driver.find_element_by_css_selector(".nav")
hidden_submenu = driver.find_element_by_css_selector(".nav #submenu1")

ActionChains(driver).move_to_element(menu).click(hidden_submenu).perform()
```

Or actions can be queued up one by one, then performed.: 

```python
menu = driver.find_element_by_css_selector(".nav")
hidden_submenu = driver.find_element_by_css_selector(".nav #submenu1")

actions = ActionChains(driver)
actions.move_to_element(menu)
actions.click(hidden_submenu)
actions.perform()
```

Either way, the actions are performed in the order they are called, one after another. 

- `__init__`(*driver*)

  Creates a new ActionChains.

  Args:

  - driver: The WebDriver instance which performs user actions.

- `click`(*on_element=None*)

  Clicks an element.

  Args:

  - on_element: The element to click. If None, clicks on current mouse position.

- `click_and_hold`(*on_element=None*)

  Holds down the left mouse button on an element.

  Args:

  - on_element: The element to mouse down. If None, clicks on current mouse position.

- `context_click`(*on_element=None*)

  Performs a context-click (right click) on an element.

  Args:

  - on_element: The element to context-click. If None, clicks on current mouse position.

- `double_click`(*on_element=None*)

  Double-clicks an element.

  Args:

  - on_element: The element to double-click. If None, clicks on current mouse position.

- `drag_and_drop`(*source*, *target*)

  Holds down the left mouse button on the source element,then moves to the target element and releases the mouse button.

  Args:

  - source: The element to mouse down.
  - target: The element to mouse up.

- `drag_and_drop_by_offset`(*source*, *xoffset*, *yoffset*)

  Holds down the left mouse button on the source element,then moves to the target offset and releases the mouse button.

  Args:

  - source: The element to mouse down.
  - xoffset: X offset to move to.
  - yoffset: Y offset to move to.

- `key_down`(*value*, *element=None*)

  Sends a key press only, without releasing it.Should only be used with modifier keys (Control, Alt and Shift).

  Args:

  - value: The modifier key to send. Values are defined in Keys class.
  - element: The element to send keys. If None, sends a key to current focused element.

  Example, pressing ctrl+c:

  ```python
  ActionChains(driver).key_down(Keys.CONTROL).send_keys('c').key_up(Keys.CONTROL).perform() 
  ```

- `key_up`(*value*, *element=None*)

  Releases a modifier key.

  Args:

  - value: The modifier key to send. Values are defined in Keys class.
  - element: The element to send keys. If None, sends a key to current focused element.

  Example, pressing ctrl+c:

  ```python
  ActionChains(driver).key_down(Keys.CONTROL).send_keys('c').key_up(Keys.CONTROL).perform()
  ```

- `move_by_offset`(*xoffset*, *yoffset*)

  Moving the mouse to an offset from current mouse position.

  Args:

  - xoffset: X offset to move to, as a positive or negative integer.
  - yoffset: Y offset to move to, as a positive or negative integer.

- `move_to_element`(*to_element*)

  Moving the mouse to the middle of an element.

  Args:

  - to_element: The WebElement to move to.

- `move_to_element_with_offset`(*to_element*, *xoffset*, *yoffset*)

  Move the mouse by an offset of the specified element.Offsets are relative to the top-left corner of the element.

  Args:

  - to_element: The WebElement to move to.
  - xoffset: X offset to move to.
  - yoffset: Y offset to move to.

- `pause`(*seconds*)

  Pause all inputs for the specified duration in seconds

- `perform`()

  Performs all stored actions.

- `release`(*on_element=None*)

  Releasing a held mouse button on an element.

  Args:

  - on_element: The element to mouse up. If None, releases on current mouse position.

- `reset_actions`()

  Clears actions that are already stored on the remote end.

- `send_keys`(**keys_to_send*)

  Sends keys to current focused element.

  Args:

  - keys_to_send: The keys to send. Modifier keys constants can be found in the ‘Keys’ class.

- `send_keys_to_element`(*element*, **keys_to_send*)

  Sends keys to an element.

  Args:

  - element: The element to send keys.
  - keys_to_send: The keys to send. Modifier keys constants can be found in the ‘Keys’ class.