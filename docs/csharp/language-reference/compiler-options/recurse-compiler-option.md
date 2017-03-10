---
title: "/recurse (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/recurse"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/recurse compiler option [C#]"
  - "recurse compiler option [C#]"
  - "-recurse compiler option [C#]"
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
caps.latest.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 12
---
# /recurse (C# Compiler Options)
\/recurse オプションを使用すると、指定のディレクトリ \(dir\) またはプロジェクト ディレクトリのすべての子ディレクトリ内のソース コード ファイルをコンパイルできます。  
  
## 構文  
  
```  
/recurse:[dir\]file  
```  
  
## Arguments  
 `dir` \(省略可能\)  
 検索を開始するディレクトリ。  指定しない場合は、プロジェクト ディレクトリから検索されます。  
  
 `file`  
 検索するファイル。  ワイルドカード文字を使用できます。  
  
## 解説  
 **\/recurse** オプションを使用すると、指定のディレクトリ \(`dir`\) またはプロジェクト ディレクトリのすべての子ディレクトリ内のソース コード ファイルをコンパイルできます。  
  
 **\/recurse** を使用しなくても、ファイル名にワイルドカードを使用すると、プロジェクト ディレクトリ内で一致するすべてのファイルをコンパイルできます。  
  
 このコンパイラ オプションは、Visual Studio で利用できず、プログラムで変更することもできません。  
  
## 使用例  
 現在のディレクトリ内のすべての C\# ファイルをコンパイルするには、次のコードを使用します。  
  
```  
csc *.cs  
```  
  
 dir1\\dir2 ディレクトリおよびそのディレクトリの下の全ディレクトリ内の C\# ファイルすべてをコンパイルし、dir2.dll を生成するには、次のコードを使用します。  
  
```  
csc /target:library /out:dir2.dll /recurse:dir1\dir2\*.cs  
```  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)