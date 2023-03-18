# 优化 PowerShell 脚本


昨天文中附的代码截图看不大清楚，是因为发文的时候发现自己的发文脚本提交草稿之后代码块的换行没有了，只剩下一行不知道多长的代码。于是花费了一些时间排查问题，发现是公众平台代码块不同于标准格式需要手动添加 `<br>` 换行符，又改进了脚本自动追加了这个换行符。

晚上继续做视频转码的时候发现昨天的 PowerShell 脚本还有瑕疵，之前因为手动转码到两位数之后开始使用脚本，这才发现一位数的时候脚本无法正常生成计数。查阅了半天也没有找到合适的解决方案，试了 ChatGPT 虽然给出答案却怎么也不好用，只好取巧先把最新文件的数字改成两位数再继续转。

之后又想起是不是可以用 GPU 转码，查了一下果然可以，转码速度提升了差不多一倍。又完善了一下脚本，把 GPU 硬转码的部分加入进去。最终的脚本暂时是这样的：

```powershell
$source_path = "F:\VIDEO_TS"
# $source_path = "F:\Documents and Settings\VIDEO_TS"
# $list = get-childitem -path $source_path\* -include vts_01*.vob -name
# 源路径后需加‘\*’，include过滤内容，name仅输出文件名
$list = get-childitem -path $source_path\* -include vts_01*.vob | Select-Object -ExpandProperty FullName
# 源路径后需加‘\*’，include过滤内容，Select-Object -ExpandProperty FullName 输出完整路径
$list_row = $list -join("|") # 将数组拼接为以‘|’分隔的字符串
$output_path = "E:\Temp\temp"
# 获取目录中数字最大的文件
$maxFile = (Get-ChildItem $output_path | Where-Object {$_.Name -match '\d+'} | Sort-Object {[int]($_.Name -replace '\D','')} -Descending)[0]
# 新文件名比最大文件数字加一
$newFileName = $maxFile.Name -replace '\d{2,}', ([int]$matches[0] + 1)
# 拼接路径
$newFilePath = Join-Path $output_path $newFileName
ffmpeg -i concat:"$list_row" -c:v hevc_nvenc $newFilePath # ffmpeg 转码命令

#Stop-Computer # 执行后关闭电脑
```

好吧，其实这篇文的一个目的是秀一下改过的代码着色格式。
