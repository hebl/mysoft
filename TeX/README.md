# TeXLive 安装

## [MacTeX](https://www.tug.org/mactex/)

安装基本版本即可

## 配置镜像源

```
tlmgr option repository http://mirrors.ustc.edu.cn/CTAN/systems/texlive/tlnet

tlmgr update --all
```

## 安装包

```
tlmgr install ctex environ trimspaces zhnumber ntheorem amsmath hyperref txfonts enumitem dirtree titlesec multirow times jknapltx symbol zapfding rsfs tipa subfigure xindy substr imakeidx datatool xfor mfirstuc everypage breakcites draftwatermark glossaries placeins tocbibind footmisc
```