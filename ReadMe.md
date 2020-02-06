離線安裝VS2019
-----
# 建立下載離線包
1. 首先用cmd移至`vs_community.exe`所在資料夾以便執行
2. 相關的參數命令可以參考[使用命令列參數安裝 Visual Studio](https://docs.microsoft.com/zh-tw/visualstudio/install/use-command-line-parameters-to-install-visual-studio?view=vs-2019)
3. 使用`--add`參數命令加入所要下載的元件，元件識別碼請參照[Visual Studio 工作負載和元件識別碼](https://docs.microsoft.com/zh-tw/visualstudio/install/workload-and-component-ids?view=vs-2019)，其中[Community 2019的元件目錄](https://docs.microsoft.com/zh-tw/visualstudio/install/workload-component-id-vs-community?vs-2019&view=vs-2019)
4. e.g.(開啟cmd輸入以下，假設本機存在：
D:\Download\vs_community__477180316.1572016098.exe)
```cmd
cd D:\Download
vs_community__477180316.1572016098.exe --layout D:\Download\vslayout ^
--add Microsoft.VisualStudio.Workload.NativeDesktop ^
--add Microsoft.VisualStudio.Workload.NativeCrossPlat ^
--add Microsoft.VisualStudio.Component.VC.CMake.Project ^
--add Microsoft.VisualStudio.Component.VC.Llvm.Clang ^
--add Microsoft.VisualStudio.Component.VC.Llvm.ClangToolset ^
--addProductLang zh-CN ^
--addProductLang zh-TW ^
--addProductLang en-US ^
--includeRecommended --lang zh-CN zh-TW en-US
```
註解：
`--layout`表示要將離線安裝包下載至的路徑
語言參數可參照[語言地區設定清單](https://docs.microsoft.com/zh-tw/visualstudio/install/create-an-offline-installation-of-visual-studio?view=vs-2019#list-of-language-locales)

# 安裝離線安裝包
1. 開啟`cmd`移動至離線安裝包路徑，執行以下命令：保險起見，最好用管理員身分啟動`cmd`
```cmd
cd D:\Download\vslayout
vs_community__477180316.1572016098.exe --installPath "D:\Program_Files\Microsoft Visual Studio\2019\Community" ^
--add Microsoft.VisualStudio.Workload.NativeDesktop ^
--add Microsoft.VisualStudio.Workload.NativeCrossPlat ^
--add Microsoft.VisualStudio.Component.VC.CMake.Project ^
--add Microsoft.VisualStudio.Component.VC.Llvm.Clang ^
--add Microsoft.VisualStudio.Component.VC.Llvm.ClangToolset ^
--includeRecommended --noWeb --nocache
```
註解：
`--installPath`設定所要安裝的路徑

<font color=#ff0000>以上命令失敗了，直接在離線包目錄下執行`vs_setup.exe`執行安裝</font>

`--noWeb`安裝程式會使用版面配置目錄中的檔案來安裝 Visual Studio。 如果使用者嘗試安裝不在版面配置中的元件，安裝程式會失敗。

`--includeRecommended`包含所安裝之任何工作負載的**建議**元件，但不包含**選擇性**元件。

`--nocache`套件會在安裝或修復之後刪除。

可以加上以下命令參數來執行安裝，具體參閱[使用命令列參數安裝 Visual Studio](https://docs.microsoft.com/zh-tw/visualstudio/install/command-line-parameter-examples?view=vs-2019#using---installpath)

`--passive --norestart` <font color=#00af00>不顯示互動式提示，但會顯示進度</font>

* 使用命令列更新 Visual Studio 執行個體，不顯示互動式提示，但顯示進度
```
vs_community__477180316.1572016098.exe --update --quiet --wait
vs_community__477180316.1572016098.exe update --wait --passive --norestart ^
--installPath "D:\Program_Files\Microsoft Visual Studio\2019\Community" ^
--add Microsoft.VisualStudio.Workload.NativeDesktop ^
--add Microsoft.VisualStudio.Workload.NativeCrossPlat ^
--add Microsoft.VisualStudio.Component.VC.CMake.Project ^
--add Microsoft.VisualStudio.Component.VC.Llvm.Clang ^
--add Microsoft.VisualStudio.Component.VC.Llvm.ClangToolset ^
--includeRecommended --nocache
```
<table><tr><td bgcolor=#ff1aff><font color=#ffffff size=3> 注意

兩個命令都是必要的。 第一個命令更新 Visual Studio 安裝程式。 第二個命令更新 Visual Studio 執行個體。 若要避免 [使用者帳戶控制] 對話方塊，請以系統管理員身分執行命令提示字元。</font></td></tr></table>