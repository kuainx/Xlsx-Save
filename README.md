# Xlsx-Style-Save
Save Xlsx with sheetjs (include style)

# English
* Navigate to [README_EN.md](./README_EN.md)

# 产生原因
* 最新版本的 [SheetJS/js-Xlsx(Github)](https://github.com/SheetJS/js-xlsx) / [官网](https://sheetjs.com/) 的Xlsx.js没有提供保存/读取格式的功能
* 他们提供了一个[Professional Edition](https://sheetjs.com/pro)，但是我并没有找到能够获取的方法
* 需求：格式的保存，不要求读取

# 解决方案
* 使用最新版本SheetJS/js-Xlsx（以下简称new ver）进行读取操作，以外部html（以下简称outer）包含
* 使用过往版本?的js-Xlsx（以下简称old ver）进行保存操作，以内部html（以下简称inner）包含
* inner使用iframe嵌入至outer
* 使用js手动添加样式
 
# 方案
* 在outer使用new ver 进行读取（使用h5的拖拽文件），转换成为JSON
* 在outer进行数据（JSON格式）的处理
* 在outer生成单元格合并数据
* 在outer将处理后的数据（JSON）使用new ver生成表格格式，但不进行保存
* 在outer根据表格的单元格号逐一附加样式属性（也可写默认值），并附加至处理后的JSON，同时附加表格合并数据
* 从outer使用H5的postMessage传递文本化JSON数据至inner
* 在inner创建表（JSON），并使用JSON将原表信息覆盖
* 在inner使用FileSaver（也可是原生js方法）将文件下载
 
# 其他
* 同域的父页面是可以直接调用iframe子页面的方法的，可以被替换
* 为兼容跨域请求，使用postMessage，在非H5浏览器必须被替换

# 更新日志
### `2018/08/17`
* 更新code_demo/inner.html，修复重复项的bug

### `2018/08/14`
* 更新readme.md
* 更新readme_EN.md
* 更新code_origin
* 更新code_demo
