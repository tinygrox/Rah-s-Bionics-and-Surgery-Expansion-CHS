# Rah's Bionics and Surgery Expansion CHS

Rimworld模组 - Rah's Bionics and Surgery Expansion的简中翻译。

同时适用于 Rah's Bionics and Surgery Expansion 和 Rah's Bionics and Surgery Expansion Hardcore Edition。

即启用 RBSE 时就是 RBSE 的翻译，启用 RBSEHC 时就是 RBSEHC 的翻译。

## 附：一个 mod 同时翻译两个版本的操作（以本项目为例）

* 操作前提：准备好了一个mod模板，并且已经准备好了2个版本的翻译文件（只留Languages文件夹就好），此时mod目录下应只存在3个文件夹【About】、【RBSE】、【RBSECH】

mod根目录下创建一个名称为`LoadFolders.xml`文件，内容如本项目：

```xml
<?xml version="1.0" encoding="utf-8"?>
<loadFolders>
  <v1.4>
    <li IfModActive="Rah.RBSE">RBSE</li>
    <li IfModActive="Rah.RBSEHC">RBSEHC</li>
  </v1.4>
</loadFolders>
```

内容解析：

```xml
<v1.4>
    <li IfModActive="Rah.RBSE">RBSE</li>
    <li IfModActive="Rah.RBSEHC">RBSEHC</li>
</v1.4>
```

此内容告诉游戏，当游戏版本为1.4时，根据mod启用的不同加载的是哪个目录下的文件。利用了`IfModActive`属性，等于号后面为 mod 的 packageID，示例为当启用的是mod为RBSE的普通版本时，加载mod根目录下的RBSE文件夹，如果是硬核版本，则加载RBSEHC文件夹。

**一些解释**

---

`IfModActive` - 当指定的mod启用时，加载指定的目录

`IfModNotActive` - 当指定的mod未启用时，加载指定的目录。

小技巧：添加多个指定的目录可以去除大量冗余的文本，例如我现在把两个版本的相同的文本全部拿出来放在根目录下的Common文件夹内，两个RBSE和RBSEHC的文件内都是不同的内容，此时我可以这样做：

```xml
<?xml version="1.0" encoding="utf-8"?>
<loadFolders>
    <v1.4>
        <li IfModActive="Rah.RBSE">Common</li>
        <li IfModActive="Rah.RBSE">RBSE</li>
        <li IfModActive="Rah.RBSEHC">Common</li>
        <li IfModActive="Rah.RBSEHC">RBSEHC</li>
    </v1.4>
</loadFolders>
```

这样操作后，无论哪个版本都会加载Common文件夹下的内容，而RBSE和RBSEHC就不用总是包含大量的重复文件，就可以去除冗余文本，让自己的mod容量更小，节省空间。

缺点：烦人，我就没弄。

更多操作请看：

https://rimworldwiki.com/wiki/Modding_Tutorials/Mod_folder_structure 页面的 `Targeting specific game versions`一节

和泰南的小本本：（看到链接带 google 你懂什么意思了吧？）

https://docs.google.com/document/d/e/2PACX-1vSOOrF961tiBuNBIr8YpUvCWYScU-Wer3h3zaoMrw_jc8CCjMjlMzNCAfZZHTI2ibJ7iUZ9_CK45IhP/pub 页面的Conditional load folders

