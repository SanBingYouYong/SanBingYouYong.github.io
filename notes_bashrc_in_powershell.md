# Windows Terminal bashrc-like Customization

- 使用`echo $PROFILE` 查看你的Windows Terminal使用的是哪个 `profile.ps1` 文件

    ![image.png](assets/img/echo_profile.png)

- 允许本地编写的脚本，搜索关键词：remote signed
- 使用 `. $PROFILE` 来像 `source ~/.bashrc` 一样让你的改动生效，或重启终端
- 定义常量 （ `export xxx=xxxxxx`）：`Set-Variable -Name “xxx” -Value “xxxxxxx” -Option Constant`
    - 就可以使用$xxx来使用他们了
    - 或者直接使用 `$xxx = xxxxxx`
- 定义方法（ `alias f="xxxx"`）：`function f { xxxx }`
    - 这方面大模型玩的比你溜
    - 比如：
        - 快速打开你的神奇妙妙工具库：
            ```powershell
            function proj {
                param (
                    [string]$projName,
                    [switch]$vscode,
                    [switch]$explorer
                )

                if ($projName) {
                    $projPath = Join-Path -Path $funpy -ChildPath $projName
                    if (Test-Path $projPath) {
                        Set-Location $projPath
                        if ($explorer) {
                            explorer.exe .
                        }
                        if ($vscode -or -not $explorer) {
                            code .
                        }
                    } else {
                        Write-Error "The project '$projName' does not exist."
                    }
                } else {
                    Get-ChildItem -Path $funpy -Directory | ForEach-Object { $_.Name }
                }
            }
            ```

- 你说的很好，但是定义了这么多，我忘了怎么办？
    - [https://stackoverflow.com/questions/15694338/how-to-get-a-list-of-custom-powershell-functions](https://stackoverflow.com/questions/15694338/how-to-get-a-list-of-custom-powershell-functions)：

        ```powershell
        # get custom functions
        $sysfunctions = Get-ChildItem function:
        function custom {Get-ChildItem function: | Where-Object {$sysfunctions -notcontains $_} }
        ```

- 不够elegante？
    - 手写或让大模型代工一个 `profile.ps1` 的文档，比如 `readme.md`
    - 在本地python环境安装[streamlit](https://streamlit.io/)
    - 编写以下简单streamlit网页简单粗暴的读取md并展示
    
        ```python
        import streamlit as st
        import os
        import subprocess

        # Set the page configuration to use the wide layout
        st.set_page_config(layout="centered")

        # Retrieve the profilePath variable from PowerShell
        # 确保你在环境变量里或profile.ps1里定义了profilePath路径，也就是你的$PROFILE住的文件夹
        profile_path = subprocess.check_output(['powershell', '-Command', '(Get-Variable -Name profilePath).Value'], text=True).strip()

        doc_path = os.path.join(profile_path, 'readme.md')

        with open(doc_path, 'r', encoding='utf-8') as file:
            readme_content = file.read()

        st.markdown(readme_content)
        ```

    - 以及定义一个简单的function来取代手打指令

        ```powershell
        function doc {
            $doc_py_path = Join-Path -Path $profilePath -ChildPath "doc.py"
            streamlit run $doc_py_path
        }
        ```

- 那么你就可以简单打一个 `doc` 在命令行里，就获得：

![image.png](assets/img/st_doc_show.png)