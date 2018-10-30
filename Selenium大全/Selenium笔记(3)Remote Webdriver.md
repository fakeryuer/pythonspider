# Selenium笔记（3）Remote Webdriver

本文集链接：https://www.jianshu.com/nb/25338984 



## 简介

`selenium.webdriver.remote.webdriver.WebDriver` 这个类其实是所有其他Webdriver的父类，例如`Chrome Webdriver`，`Firefox Webdriver`都是继承自这个类。这个类中实现了每个Webdriver间相通的方法。



## 常用操作

- `get(url)`

  在当前浏览器会话中访问传入的url地址。

  用法：

  ```python
  driver.get('https://www.baidu.com')
  ```

- `close()`

  关闭浏览器当前窗口。

- `quit()`

  退出webdriver并关闭所有窗口。

- `refresh()`

  刷新当前页面。 

- `title`

  获取当前页的标题。

- `page_source`

  获取当前页渲染后的源代码。

- `current_url`

  获取当前页面的url。

- `window_handles`

  获取当前会话中所有窗口的句柄。



## 查找元素

`Webdriver`对象中内置了查找节点元素的方法，使用非常方便。

### 单个查找

以下是查找单个元素的方法：

| 方法                                  | 作用                         |
| ------------------------------------- | ---------------------------- |
| `find_element_by_xpath`()             | 通过`Xpath`查找              |
| `find_element_by_class_name`()        | 通过`class属性`查找          |
| `find_element_by_css_selector`()      | 通过`css选择器`查找          |
| `find_element_by_id`()                | 通过`id`查找                 |
| `find_element_by_link_text`()         | 通过`链接文本`查找           |
| `find_element_by_name`()              | 通过`name属性`进行查找       |
| `find_element_by_partial_link_text`() | 通过`链接文本的部分匹配`查找 |
| `find_element_by_tag_name`()          | 通过`标签名`查找             |

查找后返回的是一个`Webelement`对象。

### 多个查找

上面的方法都是将第一个找到的元素进行返回，而将所有匹配的元素进行返回使用的是`find_elements_by_*`方法。

**注：将其中的element加上一个s，则是对应的多个查找方法。**

此方法返回的是一个`Webelement`对象组成的列表。

### 通过私有方法进行查找

除了以上的多种查找方式，还有两种私有方法`find_element()`和`find_elements()`可以使用：

例子：

```python
from selenium.webdriver.common.by import By

driver.find_element(By.XPATH, '//button[text()="Some text"]')
driver.find_elements(By.XPATH, '//button')
```

`By`这个类是专门用来查找元素时传入的参数，这个类中有以下属性：

```python
ID = "id"
XPATH = "xpath"
LINK_TEXT = "link text"
PARTIAL_LINK_TEXT = "partial link text"
NAME = "name"
TAG_NAME = "tag name"
CLASS_NAME = "class name"
CSS_SELECTOR = "css selector"
```



## 操作Cookie

- `add_cookie(cookie_dict)` 

  给当前会话添加一个cookie。

  - cookie_dict: 一个字典对象，必须要有"name"和"value"两个键，可选的键有：“path”, “domain”, “secure”, “expiry” 。

  - 用法：

    ```python
    driver.add_cookie({‘name’ : ‘foo’, ‘value’ : ‘bar’})
    driver.add_cookie({‘name’ : ‘foo’, ‘value’ : ‘bar’, ‘path’ : ‘/’})
    driver.add_cookie({‘name’ : ‘foo’, ‘value’ : ‘bar’, ‘path’ : ‘/’, ‘secure’:True})
    ```

- `get_cookie(name)`

  按name获取单个Cookie，没有则返回None。

- `get_cookies()`

  获取所有Cookie，返回的是一组字典。

- `delete_all_cookies`()[¶](http://selenium-python.readthedocs.io/api.html#selenium.webdriver.remote.webdriver.WebDriver.delete_all_cookies)

  删除所有Cookies。

- `delete_cookie`(*name*)

  按name删除指定cookie。



## 获取截屏

- `get_screenshot_as_base64()`

  获取当前窗口的截图保存为一个base64编码的字符串。

- `get_screenshot_as_file(filename)`

  获取当前窗口的截图保存为一个png格式的图片，filename参数为图片的保存地址，最后应该以.png结尾。如果出现IO错误，则返回False。

  用法：

  ```python
  driver.get_screenshot_as_file(‘/Screenshots/foo.png’)
  ```

- `get_screenshot_as_png()`

  获取当前窗口的截图保存为一个png格式的二进制字符串。



## 获取窗口信息

- `get_window_position`(*windowHandle='current'*)

  获取当前窗口的x,y坐标。

- `get_window_rect()` 

  获取当前窗口的x,y坐标和当前窗口的高度和宽度。

- `get_window_size`(*windowHandle='current'*) 

  获取当前窗口的高度和宽度。



## 切换

- `switch_to_frame`(*frame_reference*)

  将焦点切换到指定的子框架中

- `switch_to_window`(*window_name*)

  切换窗口



## 执行JS代码

- `execute_async_script(script, *args)` 

  在当前的window/frame中`异步`执行JS代码。

  script：是你要执行的JS代码。

  *args：是你的JS代码执行要传入的参数。

  用法：

  ```python
  script = “var callback = arguments[arguments.length - 1]; ”
  script2 = “window.setTimeout(function(){ callback(‘timeout’) }, 3000);” 
  driver.execute_async_script(script + script2)
  ```

- `execute_script(script, *args)` 

  在当前的window/frame中`同步`执行JS代码。

  script：是你要执行的JS代码。

  *args：是你的JS代码执行要传入的参数。



## 完整文档

*class* `selenium.webdriver.remote.webdriver.``WebDriver`(*command_executor='http://127.0.0.1:4444/wd/hub'*, *desired_capabilities=None*, *browser_profile=None*, *proxy=None*, *keep_alive=False*, *file_detector=None*, *options=None*)

Bases: `object`

Controls a browser by sending commands to a remote server. This server is expected to be running the WebDriver wire protocol as defined at

<https://github.com/SeleniumHQ/selenium/wiki/JsonWireProtocol> 。

- **Attributes:**

  - session_id - String ID of the browser session started and controlled by this WebDriver.

  - capabilities - Dictionaty of effective capabilities of this browser session as returned

    by the remote server. See <https://github.com/SeleniumHQ/selenium/wiki/DesiredCapabilities>

  - command_executor - remote_connection.RemoteConnection object used to execute commands.

  - error_handler - errorhandler.ErrorHandler object used to handle errors. 

- `__init__`(*command_executor='http://127.0.0.1:4444/wd/hub'*, *desired_capabilities=None*, *browser_profile=None*, *proxy=None*, *keep_alive=False*, *file_detector=None*, *options=None*)

  Create a new driver that will issue commands using the wire protocol.

  **Args:**

  -  command_executor - Either a string representing URL of the remote server or a customremote_connection.RemoteConnection object. Defaults to ‘<http://127.0.0.1:4444/wd/hub>’.
  - desired_capabilities - A dictionary of capabilities to request whenstarting the browser session. Required parameter.
  - browser_profile - A selenium.webdriver.firefox.firefox_profile.FirefoxProfile object.Only used if Firefox is requested. Optional.
  - proxy - A selenium.webdriver.common.proxy.Proxy object. The browser session willbe started with given proxy settings, if possible. Optional.
  - keep_alive - Whether to configure remote_connection.RemoteConnection to useHTTP keep-alive. Defaults to False.
  - file_detector - Pass custom file detector object during instantiation. If None,then default LocalFileDetector() will be used.
  - options - instance of a driver options.Options class 

- `add_cookie`(*cookie_dict*)

  Adds a cookie to your current session.

  **Args:**

  - cookie_dict: A dictionary object, with required keys - “name” and “value”;optional keys - “path”, “domain”, “secure”, “expiry”

  **Usage:**

  ```python
  driver.add_cookie({‘name’ : ‘foo’, ‘value’ : ‘bar’})
  driver.add_cookie({‘name’ : ‘foo’, ‘value’ : ‘bar’, ‘path’ : ‘/’})
  driver.add_cookie({‘name’ : ‘foo’, ‘value’ : ‘bar’, ‘path’ : ‘/’, ‘secure’:True})
  ```

- `back`()

  Goes one step backward in the browser history.

  **Usage:**

  driver.back()

- `close`()

  Closes the current window.Usage:driver.close()

- `create_web_element`(*element_id*)

  Creates a web element with the specified element_id.

- `delete_all_cookies`()

  Delete all cookies in the scope of the session.

  **Usage:**

  driver.delete_all_cookies()

- `delete_cookie`(*name*)

  Deletes a single cookie with the given name.

  **Usage:**

  driver.delete_cookie(‘my_cookie’)

- `execute`(*driver_command*, *params=None*)

  Sends a command to be executed by a command.CommandExecutor.

  **Args:**

  - driver_command: The name of the command to execute as a string.
  - params: A dictionary of named parameters to send with the command.

  **Returns:**

  The command’s JSON response loaded into a dictionary object.

- `execute_async_script`(*script*, **args*)

  Asynchronously Executes JavaScript in the current window/frame.

  **Args:**

  - script: The JavaScript to execute.
  - *args: Any applicable arguments for your JavaScript.

  **Usage:**

  ```python
  script = “var callback = arguments[arguments.length - 1]; ” “window.setTimeout(function(){ callback(‘timeout’) }, 3000);”
  driver.execute_async_script(script)
  ```

- `execute_script`(*script*, **args*)

  Synchronously Executes JavaScript in the current window/frame.

  **Args:**

  - script: The JavaScript to execute.
  - *args: Any applicable arguments for your JavaScript.

  **Usage:**

  ```python
  driver.execute_script(‘return document.title;’)
  ```

- `file_detector_context`(**args*, **\*kwds*)

  Overrides the current file detector (if necessary) in limited context. Ensures the original file detector is set afterwards.

  **Example:**

  ```python
  with webdriver.file_detector_context(UselessFileDetector):
      someinput.send_keys(‘/etc/hosts’)
  ```

  **Args:**

  - file_detector_class - Class of the desired file detector. If the class is differentfrom the current file_detector, then the class is instantiated with args and kwargs and used as a file detector during the duration of the context manager.
  - args - Optional arguments that get passed to the file detector class duringinstantiation.
  - kwargs - Keyword arguments, passed the same way as args.

- `find_element`(*by='id'*, *value=None*)

  ‘Private’ method used by the `find_element_by_*` methods.

  **Usage:**

  Use the corresponding `find_element_by_*` instead of this.

  **Return type:**

  `WebElement`

- `forward`()

  Goes one step forward in the browser history.

  Usage:

  driver.forward()

- `fullscreen_window`()

  Invokes the window manager-specific ‘full screen’ operation

- `get`(*url*)

  Loads a web page in the current browser session.

- `get_cookie`(*name*)

  Get a single cookie by name. Returns the cookie if found, None if not.

  Usage:

  driver.get_cookie(‘my_cookie’)

- `get_cookies`()

  Returns a set of dictionaries, corresponding to cookies visible in the current session.

  Usage:

  driver.get_cookies()

- `get_log`(*log_type*)

  Gets the log for a given log type

  Args:

  - log_type: type of log that which will be returned

  Usage:

  driver.get_log(‘browser’) driver.get_log(‘driver’) driver.get_log(‘client’) driver.get_log(‘server’)

- `get_screenshot_as_base64`()

  Gets the screenshot of the current window as a base64 encoded stringwhich is useful in embedded images in HTML.

  Usage:

  driver.get_screenshot_as_base64()

- `get_screenshot_as_file`(*filename*)

  Saves a screenshot of the current window to a PNG image file. ReturnsFalse if there is any IOError, else returns True. Use full paths in your filename.

  Args:

  - filename: The full path you wish to save your screenshot to. This should end with a .png extension.

  Usage:

  driver.get_screenshot_as_file(‘/Screenshots/foo.png’)

- `get_screenshot_as_png`()

  Gets the screenshot of the current window as a binary data.

  Usage:

  driver.get_screenshot_as_png()

- `get_window_position`(*windowHandle='current'*)

  Gets the x,y position of the current window.

  Usage:

  driver.get_window_position()

- `get_window_rect`()

  Gets the x, y coordinates of the window as well as height and width of the current window.

  Usage:

  driver.get_window_rect()

- `get_window_size`(*windowHandle='current'*)

  Gets the width and height of the current window.

  Usage:

  driver.get_window_size()

- `implicitly_wait`(*time_to_wait*)

  Sets a sticky timeout to implicitly wait for an element to be found,or a command to complete. This method only needs to be called one time per session. To set the timeout for calls to execute_async_script, see set_script_timeout.

  Args:

  - time_to_wait: Amount of time to wait (in seconds)

  Usage:

  driver.implicitly_wait(30)

- `maximize_window`()

  Maximizes the current window that webdriver is using

- `minimize_window`()

  Invokes the window manager-specific ‘minimize’ operation

- `quit`()

  Quits the driver and closes every associated window.

  Usage:

  driver.quit()

- `refresh`()

  Refreshes the current page.

  Usage:

  driver.refresh()

- `save_screenshot`(*filename*)

  Saves a screenshot of the current window to a PNG image file. ReturnsFalse if there is any IOError, else returns True. Use full paths in your filename.

  Args:

  - filename: The full path you wish to save your screenshot to. This should end with a .png extension.

  Usage:

  driver.save_screenshot(‘/Screenshots/foo.png’)

- `set_page_load_timeout`(*time_to_wait*)

  Set the amount of time to wait for a page load to completebefore throwing an error.

  Args:

  - time_to_wait: The amount of time to wait

  Usage:

  driver.set_page_load_timeout(30)

- `set_script_timeout`(*time_to_wait*)

  Set the amount of time that the script should wait during anexecute_async_script call before throwing an error.

  Args:

  - time_to_wait: The amount of time to wait (in seconds)

  Usage:

  driver.set_script_timeout(30)

- `set_window_position`(*x*, *y*, *windowHandle='current'*)

  Sets the x,y position of the current window. (window.moveTo)

  Args:

  - x: the x-coordinate in pixels to set the window position
  - y: the y-coordinate in pixels to set the window position

  Usage:

  driver.set_window_position(0,0)

- `set_window_rect`(*x=None*, *y=None*, *width=None*, *height=None*)

  Sets the x, y coordinates of the window as well as height and width of the current window.

  Usage:

  driver.set_window_rect(x=10, y=10) driver.set_window_rect(width=100, height=200) driver.set_window_rect(x=10, y=10, width=100, height=200)

- `set_window_size`(*width*, *height*, *windowHandle='current'*)

  Sets the width and height of the current window. (window.resizeTo)

  Args:

  - width: the width in pixels to set the window to
  - height: the height in pixels to set the window to

  Usage:

  driver.set_window_size(800,600)

- `start_client`()

  Called before starting a new session. This method may be overridden to define custom startup behavior.

- `start_session`(*capabilities*, *browser_profile=None*)

  Creates a new session with the desired capabilities.

  Args:

  - browser_name - The name of the browser to request.
  - version - Which browser version to request.platform - Which platform to request the browser on.
  - javascript_enabled - Whether the new session should support JavaScript.
  - browser_profile - A selenium.webdriver.firefox.firefox_profile.FirefoxProfile object. Only used if Firefox is requested.

- `stop_client`()

  Called after executing a quit command. This method may be overridden to define custom shutdown behavior.

- `switch_to_active_element`()

  Deprecated use driver.switch_to.active_element

- `switch_to_alert`()

  Deprecated use driver.switch_to.alert

- `switch_to_default_content`()

  Deprecated use driver.switch_to.default_content

- `switch_to_frame`(*frame_reference*)

  Deprecated use driver.switch_to.frame

- `switch_to_window`(*window_name*)

  Deprecated use driver.switch_to.window

- `application_cache`

  Returns a ApplicationCache Object to interact with the browser app cache

- `current_url`

  Gets the URL of the current page.

  Usage:

  driver.current_url

- `current_window_handle`

  Returns the handle of the current window.

  Usage:

  driver.current_window_handle

- `desired_capabilities`

  returns the drivers current desired capabilities being used

- `file_detector`


- `log_types`

  Gets a list of the available log types

  Usage:

  driver.log_types

- `mobile`


- `name`

  Returns the name of the underlying browser for this instance.

  Usage:

  name = driver.name

- `orientation`

  Gets the current orientation of the device

  Usage:

  orientation = driver.orientation

- `page_source`

  Gets the source of the current page.

  Usage:

  driver.page_source

- `switch_to`

  Returns:

  - SwitchTo: an object containing all options to switch focus into

  Usage:

  element = driver.switch_to.active_element alert = driver.switch_to.alert driver.switch_to.default_content() driver.switch_to.frame(‘frame_name’) driver.switch_to.frame(1) driver.switch_to.frame(driver.find_elements_by_tag_name(“iframe”)[0]) driver.switch_to.parent_frame() driver.switch_to.window(‘main’)

- `title`

  Returns the title of the current page.

  Usage:

  title = driver.title

- `window_handles`

  Returns the handles of all windows within the current session.

  Usage:

  driver.window_handles