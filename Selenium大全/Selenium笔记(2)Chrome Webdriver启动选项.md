# Selenium笔记（2）Chrome Webdriver启动选项

本文集链接：https://www.jianshu.com/nb/25338984 



在`Selenium`中使用不同的`Webdriver`可能会有不一样的方法，有些相同的操作会得到不一样的结果，本文主要介绍的是`Chrome()`的使用方法。

其他`Webdriver`可以查阅官方文档。



## Chrome WebDriver Options



### 简介

这是一个Chrome的参数对象，在此对象中使用`add_argument() `方法可以添加启动参数，添加完毕后可以在初始化Webdriver对象时将此Options对象传入，则可以实现以特定参数启动Chrome。



### 例子

```python
from selenium import webdriver
from selenium.webdriver.chrome.options import Options

# 实例化一个启动参数对象
chrome_options = Options()
# 添加启动参数
chrome_options.add_argument('--window-size=1366,768')
# 将参数对象传入Chrome，则启动了一个设置了窗口大小的Chrome
browser = webdriver.Chrome(chrome_options=chrome_options)
```



### 常用的启动参数

|        启动参数        |                 作用                 |
| :--------------------: | :----------------------------------: |
|    --user-agent=""     |        设置请求头的User-Agent        |
| --window-size=1366,768 |           设置浏览器分辨率           |
|       --headless       |              无界面运行              |
|   --start-maximized    |              最大化运行              |
|      --incognito       |               隐身模式               |
|  --disable-javascript  |            禁用javascript            |
|   --disable-infobars   | 禁用浏览器正在被自动化程序控制的提示 |

完整启动参数可以到此页面查看：

https://peter.sh/experiments/chromium-command-line-switches/

#### 禁用图片加载

Chrome的禁用图片加载参数设置比较复杂，如下所示：

```python
prefs = {
    'profile.default_content_setting_values' : {
        'images' : 2
    }
}
options.add_experimental_option('prefs',prefs)
```

#### 禁用浏览器弹窗

使用浏览器时常常会有弹窗弹出，以下选项可以禁止弹窗：

```python
prefs = {  
    'profile.default_content_setting_values' :  {  
        'notifications' : 2  
     }  
}  
options.add_experimental_option('prefs',prefs) 
```



### 完整文档

*class* **selenium.webdriver.chrome.options.`Options`**

Bases: `object`

#### Method

- `__init__`()


- `add_argument`(*argument*)

  Adds an argument to the listArgs:Sets the arguments

- `add_encoded_extension`(*extension*)

  Adds Base64 encoded string with extension data to a list that will be used to extract it to the ChromeDriverArgs:extension: Base64 encoded string with extension data

- `add_experimental_option`(*name*, *value*)

  Adds an experimental option which is passed to chrome.Args:name: The experimental option name. value: The option value.

- `add_extension`(*extension*)

  Adds the path to the extension to a list that will be used to extract it to the ChromeDriverArgs:extension: path to the *.crx file

- `set_headless`(*headless=True*)

  Sets the headless argumentArgs:headless: boolean value indicating to set the headless option

- `to_capabilities`()

  Creates a capabilities with all the options that have been set andreturns a dictionary with everything

#### Values


- `KEY` *= 'goog:chromeOptions'*


- `arguments`

  Returns a list of arguments needed for the browser

- `binary_location`

  Returns the location of the binary otherwise an empty string

- `debugger_address`

  Returns the address of the remote devtools instance

- `experimental_options`

  Returns a dictionary of experimental options for chrome.

- `extensions`

  Returns a list of encoded extensions that will be loaded into chrome

- `headless`

  Returns whether or not the headless argument is set



## Chrome WebDriver对象



### 简介

这个对象继承自`selenium.webdriver.remote.webdriver.WebDriver`，这个类会在下一章讲到，Chrome的WebDriver作为子类增添了几个方法。



### 指定chromedriver.exe的位置

chromedriver.exe一般可以放在环境文件中，但是有时候为了方便部署项目，或者为了容易打包，我们可以将chromedriver.exe放到我们的项目目录中，然后在初始化Chrome Webdriver对象时，传入chromedriver.exe的路径。

如下所示：

```python
from selenium import webdriver
browser = webdriver.Chrome(executable_path='chromedriver.exe')
```



### 完整文档

*class* **selenium.webdriver.chrome.webdriver.WebDriver**(*executable_path='chromedriver'*, *port=0*, *options=None*, *service_args=None*, *desired_capabilities=None*, *service_log_path=None*, *chrome_options=None*)

Bases: `selenium.webdriver.remote.webdriver.WebDriver`

Controls the ChromeDriver and allows you to drive the browser.

You will need to download the ChromeDriver executable from<http://chromedriver.storage.googleapis.com/index.html>

- `__init__`(*executable_path='chromedriver'*, *port=0*, *options=None*, *service_args=None*, *desired_capabilities=None*, *service_log_path=None*, *chrome_options=None*)

  Creates a new instance of the chrome driver.

  Starts the service and then creates new instance of chrome driver.

  Args:

  - executable_path - path to the executable. If the default is used it assumes the executable is in the $PATHport
  - port you would like the service to run, if left as 0, a free port will be found.
  - desired_capabilities: Dictionary object with non-browser specific capabilities only, such as “proxy” or “loggingPref”.
  - options: this takes an instance of ChromeOptions

- `create_options`()


- `get_network_conditions`()

  Gets Chrome network emulation settings.

  Returns:A dict. For example:

  {‘latency’: 4, ‘download_throughput’: 2, ‘upload_throughput’: 2, ‘offline’: False}

- `launch_app`(*id*)

  Launches Chrome app specified by id.

- `quit`()

  Closes the browser and shuts down the ChromeDriver executable that is started when starting the ChromeDriver

- `set_network_conditions`(**\*network_conditions*)

  Sets Chrome network emulation settings.

  Args:

  - network_conditions: A dict with conditions specification.

  Usage:

  ```python
  driver.set_network_conditions(offline=False, latency=5, # additional latency (ms)
                                download_throughput=500 * 1024, # maximal throughput
                                upload_throughput=500 * 1024) # maximal throughput
  ```

  

  Note: ‘throughput’ can be used to set both (for download and upload).