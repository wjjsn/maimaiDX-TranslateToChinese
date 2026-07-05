[SDEZ160汉化](https://github.com/pikayan69/SDEZ1.60.ZH)|[音击汉化](https://gitea.tendokyu.moe/Chilor/mu3-chn-psds)

---

## 同时也适用于几乎所有的unity引擎游戏

 - 前往XUnity.AutoTranslator的github [releases页面](https://github.com/bbepis/XUnity.AutoTranslator/releases)下载XUnity.AutoTranslator-ReiPatcher-版本号.zip和TMP_Font_AssetBundles.zip。
 - 将两个压缩包解压到游戏目录。
 - 典型的Unity游戏文件结构可能如下：
 ```
 Game/
├── Game.exe
├── Game_Data/
│   ├── Managed/
│   │   ├── Assembly-CSharp.dll
│   │   ├── UnityEngine.dll
│   │   └── ...
│   └── ...
└── ...
```
 - 将压缩包解压到Game目录下，以maimai作为的示例如图![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/64e912775f914d669cf741013c4f9f09.png#pic_center)
 - 运行SetupReiPatcherAndAutoTranslator.exe会在当前目录生成一个快捷方式：游戏名 (Patch and Run)和一个文件夹AutoTranslator打开该文件夹里的Config.ini配置信息，修改以下内容
 ```
 [General]（括号内是我写的注释）
Language=zh（要翻译成的语言）
FromLanguage=ja（原语言，ja是日语）
[TextFrameworks]（选择要抓捕文本的类型，建议全部True，防止漏抓捕）
EnableIMGUI=True
EnableUGUI=True
EnableNGUI=True
EnableTextMeshPro=True
EnableTextMesh=True
EnableFairyGUI=True
[Behaviour]（选择替换字体和备用字体，防止翻译后出现方块字）
OverrideFontTextMeshPro=arialuni_sdf_u2018
FallbackFontTextMeshPro=arialuni_sdf_u2019
```
 - 运行游戏名 (Patch and Run)，如果游戏需要强制从启动器启动则修改启动器内容：原游戏名.exe替换为游戏名 (Patch and Run)，如maimai![](https://i-blog.csdnimg.cn/direct/d3a5a60e85f842c595ffe389c842b3e7.png#pic_center)红框内的原内容是Sinmai
 - 启动游戏，按ALT + 0：打开 XUnity自动翻译器 UI。（这是零，不是 O）![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/dd96a9699d474acdab23f99721fc817c.png#pic_center)
选择翻译器和备用翻译器，建议这两种，其他的几乎都被墙了。这时候该插件会自动抓捕游戏中的文本并机翻（如果没有请尝试按ALT + T：此插件提供的所有文本的翻译版本和未翻译版本之间的交替。），你可以在如示例图片的位置修改翻译内容。![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/23193686d6f14679870173583d6df84f.png#pic_center)
等号（=）左边为插件抓捕到的文本，右边为翻译内容，你可以修改右边的内容来进行人工翻译。
 - 但是游戏有很多文本是以图片形式呈现的（如maimai），这个插件只能翻译文本。![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/c194f707bcb34f70b9b1cd7a67c1e485.png#pic_center)
在如示例图片的路径下你能找到resources.assets，通过这个文件可以获得游戏的全部图片资源![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/88b92549528a441b9e380ce72d2a9d05.png#pic_center)
 - 通过软件[AssetStudioMod](https://github.com/astro75/AssetStudioMod)你能预览并导出图片（但是不能编辑和导入），通过软件[UABEA](https://github.com/nesrak1/UABEA/releases)可以批量导出导入图片。
打开AssetStudioMod点左上角的File再点Load file，选择resources.assets并确认就可以打开该文件。点击第二行的Asset List，再在第一行选择Filter Type，再选择TexTure2D类型，就可以看到该游戏的所有图片资源。![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/80181b90f8744bdeba9704ff9ca31455.png#pic_center)
使用UABEA打开resources.assets（注意UABEA打开resources.assets需要借用到同文件夹下的其他同类文件，只有一个resources.assets是打不开的，不要把其他文件删了）选中第一个TexTure2D类型文件，向下滚动页面，按住Shift，点击最后一个TexTure2D类型文件就可以选中所有图片![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/d842c2660adb4a72bf69e95a5c52fdb7.png#pic_center)
点击右边的Plugins，再点Batch export textures，点OK，选择导出路径，所有图片就会导出，找到有文字的图片，把它ps成中文的，将所有有文字的图片都改为中文后，点击右边的Plugins，再点Batch import textures，批量覆盖掉原来的图片。
 -  但是一个一个ps工程量太大了，像maimai这种有国服的游戏，我们可以考虑把国服的图片拿过来替换。（不能直接把国服的resources.assets直接拿过来替换，会导致内存溢出，具体的原因我也不清楚）所以我们要把国服的图片导出进行替换，同样按照上文方法导出图片，可以看到不管是国服还是日服素材都很多而且数量不一样。![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/5e71afdefa3c41099f59b8e8d4fcadc0.png#pic_center)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/4baec4e784bb43a1be7149b0d7ba9194.png#pic_center)
同一个文件导出后-后面的数字编号不同，不能直接替换。所以我们写一个程序：检查国服和日服-前面的内容是否一致，如果一致就用日服文件的名字替换国服文件的名字，这样就把同一个文件数字编号不同的问题解决了。
```python
import os
import shutil

def rename_files(folder1, folder2):
    # 获取文件夹1中的所有文件名
    files1 = os.listdir(folder1)
    print(f"Files in folder1 ({folder1}):")
    for file in files1:
        print(f" - {file}")
    
    # 创建一个字典，用于存储文件夹1中"-"之前的部分和完整文件名的对应关系
    name_dict = {}
    for file in files1:
        prefix = file.split('-')[0]
        name_dict[prefix] = file
    print("\nMapping of prefixes to file names in folder1:")
    for prefix, filename in name_dict.items():
        print(f" - {prefix}: {filename}")
    
    # 获取文件夹2中的所有文件名
    files2 = os.listdir(folder2)
    print(f"\nFiles in folder2 ({folder2}):")
    for file in files2:
        print(f" - {file}")
    
    renamed_files = 0
    for file in files2:
        prefix = file.split('-')[0]
        # 如果文件夹2中的文件名前缀在文件夹1中存在，则重命名文件夹2中的文件
        if prefix in name_dict:
            old_path = os.path.join(folder2, file)
            new_path = os.path.join(folder2, name_dict[prefix])
            if old_path != new_path:
                print(f'Renaming "{old_path}" to "{new_path}"')
                shutil.move(old_path, new_path)
                renamed_files += 1
            else:
                print(f'Skipping renaming "{old_path}" to the same name.')
        else:
            print(f'No matching prefix found for "{file}" in folder1.')
    
    print(f"\nTotal files renamed: {renamed_files}")

# 设置文件夹路径
folder1 = r'E:\unityzheteng\hh\work\1\png\jp（替换成你的地址）'
folder2 = r'E:\unityzheteng\hh\work\1\png\zh（替换成你的地址）'

# 调用函数进行重命名
rename_files(folder1, folder2)
```
保留在两个文件夹中文件名相同的文件，删除其他文件
```python
import os

def compare_and_delete(folder1, folder2):
    # 获取文件夹1和文件夹2中的所有文件名
    files1 = set(os.listdir(folder1))
    files2 = set(os.listdir(folder2))
    
    print(f"Files in folder1 ({folder1}):")
    for file in files1:
        print(f" - {file}")
    
    print(f"\nFiles in folder2 ({folder2}):")
    for file in files2:
        print(f" - {file}")
    
    deleted_files = 0
    for file in files2:
        if file in files1:
            print(f'Keeping "{file}" as it exists in both folders.')
        else:
            file_path = os.path.join(folder2, file)
            print(f'Deleting "{file_path}" as it does not exist in folder1.')
            os.remove(file_path)
            deleted_files += 1
    
    print(f"\nTotal files deleted: {deleted_files}")

# 设置文件夹路径
folder1 = r'D:\huanhua\hh\png\jp（替换成你的地址）'
folder2 = r'D:\huanhua\hh\png\zh（替换成你的地址）'

# 调用函数进行比较和删除
compare_and_delete(folder1, folder2)
```
使用UABEA将图片批量导入回去即可！

 - 有些文字你会发现使用XUnity.AutoTranslator无法抓捕到，这时候必须使用[dnSpy](https://github.com/dnSpy/dnSpy)反编译Assembly-CSharp.dll，Assembly-CSharp.dll游戏的逻辑和功能，其中也有文字。打开dnSpy，打开游戏的Assembly-CSharp.dll，在选择导出到工程，就可以获得游戏的CSharp源码![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/0956d11374b94630ad54046f6da4f066.png#pic_center)
导出为工程的是一个解决方案![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/45994a2e4b7e45d4add30fa0cfa65bfc.png#pic_center)
文件夹里面就是源码，但是用vs看不方便，我们历遍所有源码挑出日文
```py
import os
import re

def extract_japanese_text_from_cs_files(folder_path, output_file):
    # 正则表达式匹配日文字符
    japanese_pattern = re.compile(r'[\u3040-\u30ff\u4e00-\u9faf\u3400-\u4dbf]+')

    with open(output_file, 'w', encoding='utf-8') as txt_file:
        for root, _, files in os.walk(folder_path):
            for file in files:
                if file.endswith('.cs'):
                    cs_file_path = os.path.join(root, file)
                    with open(cs_file_path, 'r', encoding='utf-8') as cs_file:
                        content = cs_file.read()
                        # 提取日文内容
                        japanese_texts = japanese_pattern.findall(content)
                        if japanese_texts:
                            txt_file.write(f"--- {cs_file_path} ---\n")
                            txt_file.write('\n'.join(japanese_texts))
                            txt_file.write("\n\n")

# 使用方法
folder_path = r'E:\unityzheteng\yizhi\work\jp\csharpexport\Assembly-CSharp'  # 替换为你的文件夹路径
output_file = r'E:\unityzheteng\yizhi\work\output.txt'  # 替换为你想要的输出文件路径和文件名
extract_japanese_text_from_cs_files(folder_path, output_file)

```
在ouput.txt搜索要汉化的文字，打开dnSpy，右键要修改的部分，点击编辑类，然后进行修改。修改完成后点击编译后保存即可。![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/c947f3c358564163be01f697ef8d8d2b.png#pic_center)
## 至此就是所有的汉化教程了！

