# 还是 `python` 脚本更顺手


昨天用 `PowerShell` 实现的脚本还有不少瑕疵，但因为自己不熟悉所以写起来很费力改起来更费力，因为无知所以处处掣肘。

其实脚本逻辑并不复杂，与其与 `PowerShell` 较劲不如用自己更擅长的 `Python` 解决。于是今天没有花费太多时间就很容易写好了 `Python` 的脚本，自我感觉比 `PowerShell` 的那一个要好多了，只是可惜了一次学习 `PowerShell` 的机会。但想想可以学的东西有那么多，何必贪图每一个呢，尤其这么难学而且性价比可能不高的对象。

最终的 `Python` 脚本很简单：

```python
import os
import re

source_path = r"F:\VIDEO_TS"
target_path = r"E:\Temp\temp"
default_name = "new-video-00.mp4"

# 获取目标目录最大的文件名
max_name = max(os.listdir(target_path)) \
    if os.listdir(target_path) != [] else default_name
# 最大文件名序号加一作为新文件名
new_filename = re.sub('\d+',lambda match: "{:0>2d}"\
                      .format(int(match.group(0))+1),max_name,count=1)
# 源目录中所有符合条件的文件列表
# source_file_list = []
# for i in os.listdir(source_path):
#     if 'VTS_01' in i and i[-3:] == 'VOB':
#         source_file_list.append(os.path.join(source_path,i))
source_file_list = [os.path.join(source_path,i) \
                    for i in os.listdir(source_path) \
                    if 'VTS_01' in i and i[-3:] == 'VOB']
cmd = f'ffmpeg -i concat:"{"|".join(source_file_list)}" \
    -c:v hevc_nvenc  {os.path.join(target_path,new_filename)}' # ffmpeg 转码命令

os.system(cmd)
# os.system('shutdown /s')
```

今天还发现了发文脚本另一个 code 格式问题，稍微又完善了一下感觉顺眼许多，发布的时候应该能够看到改进。刚刚发布的时候发现代码块的换行修改仍然有问题，明天继续修改优化。

现在速度比开始时快多了，除了换盘过程也完全不需要干预，不知不觉又转完一个盘包，剩下的已经不多了。
