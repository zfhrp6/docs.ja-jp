---
title: "/noconfig (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/noconfig"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/noconfig compiler option [C#]"
  - "csc.rsp"
  - "-noconfig compiler option [C#]"
  - "noconfig compiler option [C#]"
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
caps.latest.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 11
---
# /noconfig (C# Compiler Options)
**\/noconfig** オプションは、コンパイルに csc.rsp ファイルを使用しないようにコンパイラに指示します。csc.rsp ファイルは、csc.exe ファイルと同じディレクトリにあり、そこから読み込まれます。  
  
## 構文  
  
```  
/noconfig  
```  
  
## 解説  
 csc.rsp ファイルは、.NET Framework に付属のすべてのアセンブリを参照します。  Visual Studio .NET 開発環境に含まれる実際の参照は、プロジェクトの種類に応じて異なります。  
  
 csc.rsp ファイルを変更し、csc.exe を使用したコマンド ラインからのコンパイルのたびに含める追加のコンパイラ オプションを指定できます \(**\/noconfig** オプションを除く\)。  
  
 コンパイラは、**csc** コマンドに渡されるオプションを最後に処理します。  このため、コマンド ラインに指定したオプションは、csc.rsp ファイル内の同じオプションの設定をオーバーライドします。  
  
 コンパイラで csc.rsp ファイルの設定を検索および使用しない場合は、**\/noconfig** を指定します。  
  
 このコンパイラ オプションは、Visual Studio で利用できず、プログラムで変更することもできません。  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)