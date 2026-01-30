---
icon: lucide/info
title: How to write a markdown for python code
date: 2025-12-22
authors:
  - name: zhangxige
    email: daxuekanshijie@sina.cn
categories:
  - python
---

# Virtural environment

这是我的第一篇 Zensical 博客文章！

## Manage environment

- ✅ pip/pipx
- ✅ uv(recommend)
- ✅ .env

=== ":material-apple: macOS"
    Open up a terminal window and install Zensical by first setting up a virtual
    environment and then using `pip` to install the Zensical package into it:

    ``` sh
    python3 -m venv .venv
    source .venv/bin/activate
    pip install zensical
    ```

=== ":fontawesome-brands-windows: Windows"
    Open up a Command Window and install Zensical by first setting up a virtual
    environment and then using `pip` to install the Zensical package into it:

    ```
    python3 -m venv .venv
    .venv\Scripts\activate
    pip install zensical
    ```

=== ":material-linux: Linux"
    Open up a terminal window and install Zensical by first setting up a virtual
    environment and then using `pip` to install the Zensical package into it:

    ``` sh
    python3 -m venv .venv
    source .venv/bin/activate
    pip install zensical
    ```

## Python demo

```py hl_lines="10 13"
"""scripts/site_inspect.py
用于快速统计 site 目录中文件数量与大小的脚本示例
"""
import os
from pathlib import Path

def inspect_site(path="site"):
    p = Path(path)
    if not p.exists():
        print(f"目录 {path} 不存在")
        return
    total_files = 0
    total_bytes = 0
    for root, dirs, files in os.walk(p):
        for f in files:
            total_files += 1
            fp = Path(root) / f
            total_bytes += fp.stat().st_size
    print(f"文件数: {total_files}")
    print(f"总大小: {total_bytes/1024:.2f} KB") # (1)!

if __name__ == '__main__':
    inspect_site()    
```

1. > add some examples

    If you want to load an (additional) font from another destination or override
    the system font, you can use an [Twikoo] to add the
    corresponding `@font-face` definition:

### Special Block

## Block Example

!!! example 

    === "Unordered List"

        ``` markdown
        * Sed sagittis eleifend rutrum
        * Donec vitae suscipit est
        * Nulla tempor lobortis orci
        ```

    === "Ordered List"

        ``` markdown
        1. Sed sagittis eleifend rutrum
        2. Donec vitae suscipit est
        3. Nulla tempor lobortis orci
        ```

!!! note
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor massa, nec semper lorem quam in massa.

!!! note "Outer Note"

    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

    !!! note "Inner Note"

        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
        nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
        massa, nec semper lorem quam in massa.

## Expand Demo

??? example "Expand to show alternate icon sets"

    === ":octicons-mark-github-16: Octicons"

        ``` toml
        [project.theme.icon.admonition]
        note = "octicons/tag-16"
        abstract = "octicons/checklist-16"
        info = "octicons/info-16"
        tip = "octicons/squirrel-16"
        success = "octicons/check-16"
        question = "octicons/question-16"
        warning = "octicons/alert-16"
        failure = "octicons/x-circle-16"
        danger = "octicons/zap-16"
        bug = "octicons/bug-16"
        example = "octicons/beaker-16"
        quote = "octicons/quote-16"
        ```


    === ":fontawesome-brands-font-awesome: FontAwesome"

        ``` toml
        [project.theme.icon.admonition]
        note = "fontawesome/solid/note-sticky"
        abstract = "fontawesome/solid/book"
        info = "fontawesome/solid/circle-info"
        tip = "fontawesome/solid/bullhorn"
        success = "fontawesome/solid/check"
        question = "fontawesome/solid/circle-question"
        warning = "fontawesome/solid/triangle-exclamation"
        failure = "fontawesome/solid/bomb"
        danger = "fontawesome/solid/skull"
        bug = "fontawesome/solid/robot"
        example = "fontawesome/solid/flask"
        quote = "fontawesome/solid/quote-left"
        ```
