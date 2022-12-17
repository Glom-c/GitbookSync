# 💿 插件配置

## config.yml

```yaml
#数据库配置
database:
  enable: false
  host: localhost
  port: 3306
  user: root
  password: root
  database: root
  table: my_database
options:
  #调试模式
  debug: false
  #内联函数-调试模式
  debug-function: false
  #(脚本任务)线程池容量
  thread-pool-size: 4
  #默认的数字格式
  #会影响Pouvoir的所有附属
  number-format: "#.##"
  #默认的小数精确位数
  #会影响Pouvoir的所有附属
  big-decimal-scale: 4
```

## script.yml

```yaml
#全局静态类导入
#格式:
#  变量名: '类名'
#在这里的静态类可以直接在脚本里调用
static-classes:
  Bukkit: 'org.bukkit.Bukkit'
  Arrays: 'java.util.Arrays'
  Tool: 'com.skillw.pouvoir.api.script.ScriptTool'
  Data: 'com.skillw.pouvoir.api.script.ScriptTool;object'
  Pouvoir: 'com.skillw.pouvoir.Pouvoir'
  CalculationUtils: 'com.skillw.pouvoir.util.CalculationUtils'
  MapUtils: 'com.skillw.pouvoir.util.MapUtils'
  ColorUtils: 'com.skillw.pouvoir.util.ColorUtils'
  EntityUtils: 'com.skillw.pouvoir.util.EntityUtils'
  FileUtils: 'com.skillw.pouvoir.util.FileUtils'
  ItemUtils: 'com.skillw.pouvoir.util.ItemUtils'
  GsonUtils: 'com.skillw.pouvoir.util.GsonUtils'
  MessageUtils: 'com.skillw.pouvoir.util.MessageUtils'
  NumberUtils: 'com.skillw.pouvoir.util.NumberUtils'
  PlayerUtils: 'com.skillw.pouvoir.util.PlayerUtils'
  ClassUtils: 'com.skillw.pouvoir.util.ClassUtils'
  StringUtils: 'com.skillw.pouvoir.util.StringUtils'
```

## lang/zh\_cn.yml

```yaml
plugin-prefix: '&d[&9Pouvoir&d] '
plugin-debug: '&d[&9Pouvoir-Debug&d] '
command-reload: '&d[&9Pouvoir&d] &aPouvoir 已重载!'
command-script-invoke: '&d[&9Pouvoir&d] &a正在调用脚本 &6{0} &a!'
command-script-invoke-end: "&d[&9Pouvoir&d] &e脚本 &6{0} &e返回值: &b{1} &e, 耗时 &9{2}ms"
static-class-not-found: '&d[&9Pouvoir&d] &c未发现类 &6{0} &c!'
script-compile-start: '&d[&9Pouvoir&d] &a开始编译 &6{0}&a...'
script-compile-end: '&d[&9Pouvoir&d] &a脚本 &6{0} &a编译成功! 耗时 &9{1}ms!'
script-compile-fail: '&d[&9Pouvoir&d] &c在编译 &6{0} &c时发生了错误! 请检查.'
script-file-not-found: '&d[&9Pouvoir&d] &c未发现脚本文件 &6{0} &c! 请检查.'
script-invoke-script-exception: '&d[&9Pouvoir&d] &c在调用脚本 &6{1} &c的函数 &d{0} &c时发生了错误! 任务ID: &6{2}'
script-invoke-exception: '&d[&9Pouvoir&d] &c在调用脚本 &6{1} &c的函数 &d{0} &c时发生了错误! 任务ID: &6{2}'
script-invoke-task-cancelled: '&d[&9Pouvoir&d] &c调用 &6{1} &c的函数 &d{0} &c的任务 &6{2} &c取消!'
script-invoke-wrong-format: '&d[&9Pouvoir&d] &c如果你想调用某个脚本文件的函数, 请以此格式输入: &6脚本文件名称.js::函数名 &c!'
script-engine-not-found: '&d[&9Pouvoir&d] &c未发现PouScriptEngine &6{0} &c! 请检查.'
script-engine-valid-suffix: '&d[&9Pouvoir&d] &c未发现含后缀 &6{0} &c的PouScriptEngine&c! 请检查.'
function-wrong-arguments: '&d[&9Pouvoir&d] &c调用函数 &6{0} &c时使用了错误的参数!'
pou-placeholder-register: '&d[&9Pouvoir&d] &ePou占位符 &6{0} &e注册成功! 来自: &d{1} &9{2} &eBy: &a{3}'
command-message:
  - '&6================================'
  - ' &9指令列表:'
  - '  &6/pouvoir'
  - '    &d- &ehelp &5—— &a显示帮助.'
  - '    &d- &einfo &5—— &a显示插件信息.'
  - '    &d- &erun &b脚本路径 (函数名) (参数) &5—— &a运行一个脚本函数'
  - '    &d- &ereport &5—— &a查看耗时数据'
  - '    &d- &eclear &5—— &a清除耗时数据'
  - '    &d- &etask'
  - '      &7- &einfo &5—— &a查看脚本任务信息'
  - '      &7- &estop {Task ID} &5—— &a停止一个任务'
  - '    &d- &ereload &5—— &a重载插件'
  - '  &6================================'
wrong-command-message: '&d[&9Pouvoir&d] &c你是不是输错指令啦!'
command-clear: '&d[&9Pouvoir&d] &a耗时数据已清楚!'
command-task-info: '&e正在运行的任务:'
running-task-empty: '&7没有正在运行的任务!'
command-task-stop: '&d[&9Pouvoir&d] &c任务 &6{0} 已取消!'

script-invoking-info: "&e正在调用脚本 &6{0} &e的函数 &d{1}"
script-invoking-arguments: "&e全局参数: "
script-invoking-parameters: "&e函数参数: "

annotation-listener-register: '&d[&9Pouvoir&d] &a脚本监听器 &6{0} &a注册成功!'
annotation-listener-unregister: '&d[&9Pouvoir&d] &c脚本监听器 &6{0} &c已注销!'
annotation-function-register: '&d[&9Pouvoir&d] &a脚本函数 &6{0} &a注册成功!'
annotation-function-unregister: '&d[&9Pouvoir&d] &c脚本函数 &6{0} &c已注销!'
annotation-awake-register: '&d[&9Pouvoir&d] &a脚本启动器 &6{0} &a注册成功!'
annotation-awake-unregister: '&d[&9Pouvoir&d] &c脚本启动器 &6{0} &c已注销!'
annotation-awake-running: '&d[&9Pouvoir&d] &c脚本启动器 &6{0} &c正在运行!'
annotation-annotation-register: '&d[&9Pouvoir&d] &a脚本注解 &6{0} &a注册成功!'
annotation-annotation-unregister: '&d[&9Pouvoir&d] &c脚本注解 &6{0} &c已注销!'
annotation-placeholder-register: '&d[&9Pouvoir&d] &a脚本占位符 &6{0} &a注册成功!'
annotation-placeholder-unregister: '&d[&9Pouvoir&d] &c脚本占位符 &6{0} &c已注销!'
kotlin-unit: '&7无'
class-not-found: '&d[&9Pouvoir&d] &c未发现类 &6{0} &c! 请检查.'
wrong-config: '&d[&9Pouvoir&d] &c配置文件 &6{0} &c错误! 请检查.'
wrong-config-cause: '&d[&9Pouvoir&d] &c原因: {0}'

plugin-load: '&d[&9{0}&d] &6{0} &a加载成功!'
plugin-enable: '&d[&9{0}&d] &6{0} &a启用成功!'
plugin-disable: '&d[&9{0}&d] &6{0} &c关闭成功!'
```

## lang/en\_US.yml

```yaml
plugin-prefix: '&d[&9Pouvoir&d] '
plugin-debug: '&d[&9Pouvoir-Debug&d] '
command-reload: '&d[&9Pouvoir&d] &aPouvoir have been reloaded!'
command-script-invoke: '&d[&9Pouvoir&d] &aInvoking Script &6{0} &a!'
command-script-invoke-end: "&d[&9Pouvoir&d] &eInvocation of &6{0} &ereturn: &b{0} &e, in &9{1}ms"
command-script-wrong: '&d[&9Pouvoir&d] &cThere was an error during invoking the script &6{0} &c!'
static-class-not-found: '&d[&9Pouvoir&d] &cThe class &6{0} &cdosen`t exist!'
script-compile-start: '&d[&9Pouvoir&d] &aStart to compile &6{0}&a...'
script-compile-end: '&d[&9Pouvoir&d] &aCompiled &6{0} &asuccessfully in &9{1}ms!'
script-compile-fail: '&d[&9Pouvoir&d] &cThere was an error during compiling the script &6{0} &c! Please check.'
script-file-not-found: '&d[&9Pouvoir&d] &cCan t found the script file &6{0} &c! Please check.'
script-invoke-script-exception: '&d[&9Pouvoir&d] &cError while invoke the function &6{0} &cof &d{1} &c! Task ID: &6{2}'
script-invoke-exception: '&d[&9Pouvoir&d] &cError while invoke the function &6{0} &cof &d{1} &c! Task ID: &6{2}'
script-invoke-wrong-format: '&d[&9Pouvoir&d] &cIf you wanna invoke script file`s function, you should write it in this format: &6{file`s path}.js::{function`s name} &c instead of &4{0}!'
script-engine-not-found: '&d[&9Pouvoir&d] &cCan t found the PouScriptEngine &6{0} &c! Please check.'
script-engine-valid-suffix: '&d[&9Pouvoir&d] &cCan t found the PouScriptEngine with suffix &6{0} &c! Please check.'
function-wrong-arguments: '&d[&9Pouvoir&d] &cWrong arguments while calling the function &6{0} &c!'
pou-placeholder-register: '&d[&9Pouvoir&d] &ePouPlaceholder &6{0} &ehas successfully registered! From: &d{1} &9{2} &eBy: &a{3}'
command-message:
  - '&6================================'
  - ' &9Command List:'
  - '    &d- &ehelp &5—— &aShow the help of command'
  - '    &d- &einfo &5—— &aShow the info of Pouvoir.'
  - '    &d- &erun &bscript file path function (args) &5—— &aRun a function of a script'
  - '    &d- report &5—— &aCheck Mirror Data.'
  - '    &d- clear &5—— &aClear Mirror Data'
  - '    &d- &etask'
  - '      &7- &einfo &5—— &aCheck Script Task Info.'
  - '      &7- &estop {Task ID} &5—— &aStop a running task.'
  - '    &d- &ereload &5—— &aReload Pouvoir'
  - '  &6================================'
wrong-command-message: '&d[&9Pouvoir&d] &cWrong command!'
command-clear: '&d[&9Pouvoir&d] &aMirrorData has been cleared!'
command-task-info: '&eRunning Tasks Info:'
running-task-empty: '&7No running tasks.'
command-task-stop: '&d[&9Pouvoir&d] &cTask &6{0} &chas been cancelled!'

script-invoking-info: "&eInvoking script &6{0} &e's function &d{1}"
script-invoking-arguments: "&eArguments: "
script-invoking-parameters: "&eParameters: "

annotation-listener-register: '&d[&9Pouvoir&d] &aScript Listener &6{0} &ahas been registered!'
annotation-listener-unregister: '&d[&9Pouvoir&d] &cScript Listener &6{0} &chas been unregistered!'
annotation-function-register: '&d[&9Pouvoir&d] &aScript Function &6{0} &ahas been registered!'
annotation-function-unregister: '&d[&9Pouvoir&d] &cScript Function &6{0} &chas been unregistered!'
annotation-awake-register: '&d[&9Pouvoir&d] &aScript Awake &6{0} &ahas been registered!'
annotation-awake-unregister: '&d[&9Pouvoir&d] &cScript Awake &6{0} &chas been unregistered!'
annotation-awake-running: '&d[&9Pouvoir&d] &aScript Awake &6{0} &ais running!'
annotation-annotation-register: '&d[&9Pouvoir&d] &aScript Annotation &6{0} &ahas been registered!'
annotation-annotation-unregister: '&d[&9Pouvoir&d] &cScript Annotation &6{0} &chas been unregistered!'
annotation-placeholder-register: '&d[&9Pouvoir&d] &aScript FunctionPlaceholder &6{0} &ahas been registered!'
annotation-placeholder-unregister: '&d[&9Pouvoir&d] &cScript FunctionPlaceholder &6{0} &chas been unregistered!'

kotlin-unit: '&7null'
class-not-found: '&d[&9Pouvoir&d] &cClass &6{0} &cdosen`t exist!'
wrong-config: '&d[&9Pouvoir&d] &cConfig &6{0} &cis wrong!'
wrong-config-cause: '&d[&9Pouvoir&d] &cCause: &f{0}'

plugin-load: '&d[&9{0}&d] &6{0} &ahas been loaded!'
plugin-enable: '&d[&9{0}&d] &6{0} &ahas been enabled!'
plugin-disable: '&d[&9{0}&d] &6{0} &chas been disabled!'
```
