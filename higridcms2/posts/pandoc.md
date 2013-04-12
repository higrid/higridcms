---
layout: post
title: 	使用Pandoc转换markdown等文本文档
description:  本文介绍了使用Pandoc转换markdown等文本文档的方法，pandoc就是一个很好的文本格式转换器。pandoc这种格式转换器能把我们用markdown写成的书，转换成latex格式。然后对得到的latex做一些自定义处理，最终得到我们想要的pdf输出格式的过程。。
keywords: Pandoc, Pandoc格式转换
category :  软件使用
date :  2013-04-07
tags : [教程, markdown, pandoc, 推荐]
---
 @md@ 虽然写起来方便, 但是要预览的话还要用`ReText`打开, 很多人希望有一个把 **markdown文件变成html格式** 的工具，`pandoc`就是一个很好的文本格式转换器。`pandoc`这种格式转换器能把我们用markdown写成的书，转换成latex格式。然后对得到的latex做一些自定义处理，最终得到我们想要的pdf输出格式的过程。

##为什么要进行格式转换
虽然这个问题也许没什么意义，但是实际中，确实会经常遇到各种需要 **转换格式** 的场合。以 @hi@ 为例：上面的文档是 @md@ 格式，显示是html格式，每位开发过这方面程序人都会遇到一些格式转化问题，各种格式之间需要来回转换。这个时候，pandoc就管用了。事实证明，使用Pandoc进行文本格式转换非常恰当。

HIGRID_ART_ADS

## Pandoc格式转换器介绍
基本说来，常用的格式pandoc都会支持。Pandoc输入格式可以是： @md@  ,Textile, reStructuredText, HTML,  LaTeX等，输出语言非常丰富，包括： markdown, reStructuredText, XHTML, HTML 5, LaTeX , ConTeXt,RTF, DocBook XML, OpenDocument XML, ODT, Word docx, GNU Texinfo, MediaWiki markup, EPUB, Textile, groff man, Emacs Org-Mode, AsciiDoc, Slidy, DZSlides, S5 HTML slide shows. 如果安装了 LaTeX ,甚至还可以输出为 PDF 格式！

当然，Pandoc Markdown不是万能的，表格、复杂公式、多国语言、上下标、交叉引用、图表对齐较多的场合，它并不适合。但是需要互动、实时展现、更快输出的场合，Pandoc Markdown等值得大力推荐。未来互联网会逼使写作趋简。需要更快发表、互动输出与交流的场合，也会越来越多。比如课堂作业、企业内部交流、个人博客。用它节省的时间是写作时比较关键的"创作时间"而非"排版时间"。

## Pandoc使用方法

1. 从 code.google.com/p/pandoc/downloads/list 下载适合操作系统的程序
2. 安装的话，如果是windows，一路next就好了，会自动加入到system path里面
2. 终端安装使用     `sudo apt-get install pandoc`
3. pandoc是个命令行程序，所有操作通过命令行来完成
 

## pandoc转换文本文档常用命令

###常用参数

- -f 输入格式（如果没有制定格式，则根据后缀名判断，如果没后缀名，则默认为markdown）
- -t 输输出格式（默认为html）
- -o 如果没有的话（默认是STDOUT）

###Pandoc格式转换命令

a: 转换为html格式。这里--ascii可以避免转成utf-8编码，这样中文在浏览器上就不会乱码了。命令为
	pandoc -f markdown -t html higrid.net.txt -o newfile.html
	pandoc --ascii higrid.net.txt -o newfile.html

b: 转为pdf格式。注意，为了正确转换中文文本，请修改模板文件，在模板文件第一行下方加入 `\usepackage{ctex}` 命令为
	pandoc --latex-engine=xelatex yourfile.txt -o newfile.pdf

在windows 中使用时，新建文本文档，改后缀名为cmd，然后插入这样代码：
	cd
	pandoc -f markdown -t html in.txt -o out.html
保存后双击运行，就可以自动把当前目录下in.txt文件转换为out.html文件，非常方便！
 

详细的使用说明可以查找安装目录里面的 README.html 文件！看看帮助: 

    $ pandoc -h
    pandoc [OPTIONS] [FILES]
    Input formats:  native, markdown, markdown+lhs, rst, rst+lhs, html, latex, latex+lhs
    Output formats:  native, html, html+lhs, s5, docbook, opendocument, odt, latex, latex+lhs, context, texinfo, man, markdown, markdown+lhs, plain, rst, rst+lhs, mediawiki, rtf
    Options:
      -f FORMAT, -r FORMAT  --from=FORMAT, --read=FORMAT                    
      -t FORMAT, -w FORMAT  --to=FORMAT, --write=FORMAT                     
      -s                    --standalone                                    
      -o FILENAME           --output=FILENAME                               
      -p                    --preserve-tabs                                 
                            --tab-stop=TABSTOP                              
                            --strict                                        
                            --reference-links                               
      -R                    --parse-raw                                     
      -S                    --smart                                         
      -m[URL]               --latexmathml[=URL], --asciimathml[=URL]        
                            --mathml[=URL]                                  
                            --mimetex[=URL]                                 
                            --jsmath[=URL]                                  
                            --gladtex                                       
      -i                    --incremental                                   
                            --xetex                                         
      -N                    --number-sections                               
                            --no-wrap                                       
                            --sanitize-html                                 
                            --email-obfuscation=none|javascript|references  
                            --id-prefix=STRING                              
                            --indented-code-classes=STRING                  
                            --toc, --table-of-contents                      
                            --base-header-level=LEVEL                       
                            --template=FILENAME                             
      -V FILENAME           --variable=FILENAME                             
      -c URL                --css=URL                                       
      -H FILENAME           --include-in-header=FILENAME                    
      -B FILENAME           --include-before-body=FILENAME                  
      -A FILENAME           --include-after-body=FILENAME                   
      -C FILENAME           --custom-header=FILENAME                        
      -T STRING             --title-prefix=STRING                           
                            --reference-odt=FILENAME                        
      -D FORMAT             --print-default-template=FORMAT                 
                            --data-dir=DIRECTORY                            
                            --dump-args                                     
                            --ignore-args                                   
      -v                    --version                                       
      -h                    --help       

真是more than I've expected! markdown/rst/html/latex之间可以互转!

使用pandoc命令就可以在随便转换了, 示例, 把demo.md输出成demo.html:

	`$pandoc -f markdown -t html -o demo.html demo.md`
