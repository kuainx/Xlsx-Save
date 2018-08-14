# Xlsx-Style-Save
Save Xlsx with sheetjs (include style)

# 中文
* 导航至 [README.md](./README.md)
* This translation is incomplete. Please help me translate this article from [Chinese](./README.md).

# Develop Reason
* The latest version of [SheetJS/js-Xlsx(GitHub)](https://github.com/SheetJS/js-xlsx) / [Official Website](https://sheetjs.com/) didn't provide the function of reading or saving the XLSX with style
* Although they provide a [Professional Edition](https://sheetjs.com/pro) , I can't get it.
* User Requirement(You can use this project while you need ...) : Saveing file with style , but don't need to read style

# Solution
* Use the latest version SheetJS/js-Xlsx(hereinafter called the 'new ver') to read the file
* Use the Outer HTML (hereinafter called the 'outer') to include it
* Use the past version? js-Xlsx(hereinafter called the 'old ver') to save the file
* Use the Inner HTML (hereinafter called the 'inner') to include it
* Use Iframe to embed inner into outer
* Use javascript to add style manually
 
# Method
* 在outer使用new ver 进行读取（使用h5的拖拽文件），转换成为JSON
* 在outer进行数据（JSON格式）的处理
* 在outer生成单元格合并数据
* 在outer将处理后的数据（JSON）使用new ver生成表格格式，但不进行保存
* 在outer根据表格的单元格号逐一附加样式属性（也可写默认值），并附加至处理后的JSON，同时附加表格合并数据
* 从outer使用H5的postMessage传递文本化JSON数据至inner
* 在inner创建表（JSON），并使用JSON将原表信息覆盖
* 在inner使用FileSaver（也可是原生js方法）将文件下载
 
# Other
* In the same origin , outer can use the function in the inner
* If you only use in the same origin , postMessage can be replaced
* To use the cross origin at the same time , we use the postMessage of the H5 function
* If you use the broser didn't allow HTML5 , it must be replaced

# Update log
### `2018/08/14`
* Update readme.md
* Update readme_EN.md
* Update code_origin
* Update code_demo
