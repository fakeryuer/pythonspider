# Selenium笔记（7）异常

本文集链接：https://www.jianshu.com/nb/25338984 



## 完整文档

Exceptions that may happen in all the webdriver code.

- *exception* `selenium.common.exceptions.``ElementClickInterceptedException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.WebDriverException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.WebDriverException)The Element Click command could not be completed because the element receiving the events is obscuring the element that was requested clicked.

- *exception* `selenium.common.exceptions.``ElementNotInteractableException`(*msg=None*, *screen=None*, *stacktrace=None*)[¶](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.ElementNotInteractableException)

  Bases: [`selenium.common.exceptions.InvalidElementStateException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.InvalidElementStateException)Thrown when an element is present in the DOM but interactions with that element will hit another element do to paint order

- *exception* `selenium.common.exceptions.``ElementNotSelectableException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.InvalidElementStateException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.InvalidElementStateException)Thrown when trying to select an unselectable element.For example, selecting a ‘script’ element.

- *exception* `selenium.common.exceptions.``ElementNotVisibleException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.InvalidElementStateException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.InvalidElementStateException)Thrown when an element is present on the DOM, but it is not visible, and so is not able to be interacted with.Most commonly encountered when trying to click or read text of an element that is hidden from view.

- *exception* `selenium.common.exceptions.``ErrorInResponseException`(*response*, *msg*)

  Bases: [`selenium.common.exceptions.WebDriverException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.WebDriverException)Thrown when an error has occurred on the server side.This may happen when communicating with the firefox extension or the remote driver server.`__init__`(*response*, *msg*)

- *exception* `selenium.common.exceptions.``ImeActivationFailedException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.WebDriverException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.WebDriverException)Thrown when activating an IME engine has failed.

- *exception* `selenium.common.exceptions.``ImeNotAvailableException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.WebDriverException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.WebDriverException)Thrown when IME support is not available. This exception is thrown for every IME-related method call if IME support is not available on the machine.

- *exception* `selenium.common.exceptions.``InsecureCertificateException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.WebDriverException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.WebDriverException)Navigation caused the user agent to hit a certificate warning, which is usually the result of an expired or invalid TLS certificate.

- *exception* `selenium.common.exceptions.``InvalidArgumentException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.WebDriverException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.WebDriverException)The arguments passed to a command are either invalid or malformed.

- *exception* `selenium.common.exceptions.``InvalidCookieDomainException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.WebDriverException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.WebDriverException)Thrown when attempting to add a cookie under a different domain than the current URL.

- *exception* `selenium.common.exceptions.``InvalidCoordinatesException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.WebDriverException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.WebDriverException)The coordinates provided to an interactions operation are invalid.

- *exception* `selenium.common.exceptions.``InvalidElementStateException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.WebDriverException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.WebDriverException)

- *exception* `selenium.common.exceptions.``InvalidSelectorException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.NoSuchElementException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.NoSuchElementException)Thrown when the selector which is used to find an element does not return a WebElement. Currently this only happens when the selector is an xpath expression and it is either syntactically invalid (i.e. it is not a xpath expression) or the expression does not select WebElements (e.g. “count(//input)”).

- *exception* `selenium.common.exceptions.``InvalidSessionIdException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.WebDriverException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.WebDriverException)Occurs if the given session id is not in the list of active sessions, meaning the session either does not exist or that it’s not active.

- *exception* `selenium.common.exceptions.``InvalidSwitchToTargetException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.WebDriverException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.WebDriverException)Thrown when frame or window target to be switched doesn’t exist.

- *exception* `selenium.common.exceptions.``JavascriptException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.WebDriverException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.WebDriverException)An error occurred while executing JavaScript supplied by the user.

- *exception* `selenium.common.exceptions.``MoveTargetOutOfBoundsException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.WebDriverException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.WebDriverException)Thrown when the target provided to the ActionsChains move() method is invalid, i.e. out of document.

- *exception* `selenium.common.exceptions.``NoAlertPresentException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.WebDriverException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.WebDriverException)Thrown when switching to no presented alert.This can be caused by calling an operation on the Alert() class when an alert is not yet on the screen.

- *exception* `selenium.common.exceptions.``NoSuchAttributeException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.WebDriverException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.WebDriverException)Thrown when the attribute of element could not be found.You may want to check if the attribute exists in the particular browser you are testing against. Some browsers may have different property names for the same property. (IE8’s .innerText vs. Firefox .textContent)

- *exception* `selenium.common.exceptions.``NoSuchCookieException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.WebDriverException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.WebDriverException)No cookie matching the given path name was found amongst the associated cookies of the current browsing context’s active document.

- *exception* `selenium.common.exceptions.``NoSuchElementException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.WebDriverException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.WebDriverException)Thrown when element could not be found.If you encounter this exception, you may want to check the following:Check your selector used in your find_by…Element may not yet be on the screen at the time of the find operation, (webpage is still loading) see selenium.webdriver.support.wait.WebDriverWait() for how to write a wait wrapper to wait for an element to appear.

- *exception* `selenium.common.exceptions.``NoSuchFrameException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.InvalidSwitchToTargetException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.InvalidSwitchToTargetException)Thrown when frame target to be switched doesn’t exist.

- *exception* `selenium.common.exceptions.``NoSuchWindowException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.InvalidSwitchToTargetException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.InvalidSwitchToTargetException)Thrown when window target to be switched doesn’t exist.To find the current set of active window handles, you can get a list of the active window handles in the following way:`print driver.window_handles `

- *exception* `selenium.common.exceptions.``RemoteDriverServerException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.WebDriverException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.WebDriverException)

- *exception* `selenium.common.exceptions.``ScreenshotException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.WebDriverException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.WebDriverException)A screen capture was made impossible.

- *exception* `selenium.common.exceptions.``SessionNotCreatedException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.WebDriverException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.WebDriverException)A new session could not be created.

- *exception* `selenium.common.exceptions.``StaleElementReferenceException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.WebDriverException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.WebDriverException)Thrown when a reference to an element is now “stale”.Stale means the element no longer appears on the DOM of the page.Possible causes of StaleElementReferenceException include, but not limited to:You are no longer on the same page, or the page may have refreshed since the element was located.The element may have been removed and re-added to the screen, since it was located. Such as an element being relocated. This can happen typically with a javascript framework when values are updated and the node is rebuilt.Element may have been inside an iframe or another context which was refreshed.

- *exception* `selenium.common.exceptions.``TimeoutException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.WebDriverException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.WebDriverException)Thrown when a command does not complete in enough time.

- *exception* `selenium.common.exceptions.``UnableToSetCookieException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.WebDriverException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.WebDriverException)Thrown when a driver fails to set a cookie.

- *exception* `selenium.common.exceptions.``UnexpectedAlertPresentException`(*msg=None*, *screen=None*, *stacktrace=None*, *alert_text=None*)

  Bases: [`selenium.common.exceptions.WebDriverException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.WebDriverException)Thrown when an unexpected alert is appeared.Usually raised when when an expected modal is blocking webdriver form executing any more commands.`__init__`(*msg=None*, *screen=None*, *stacktrace=None*, *alert_text=None*)

- *exception* `selenium.common.exceptions.``UnexpectedTagNameException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.WebDriverException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.WebDriverException)Thrown when a support class did not get an expected web element.

- *exception* `selenium.common.exceptions.``UnknownMethodException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: [`selenium.common.exceptions.WebDriverException`](http://selenium-python.readthedocs.io/api.html#selenium.common.exceptions.WebDriverException)The requested command matched a known URL but did not match an method for that URL.

- *exception* `selenium.common.exceptions.``WebDriverException`(*msg=None*, *screen=None*, *stacktrace=None*)

  Bases: `exceptions.Exception`Base webdriver exception.`__init__`(*msg=None*, *screen=None*, *stacktrace=None*)