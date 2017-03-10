---
title: "/main (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/main"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-main compiler option [C#]"
  - "main compiler option [C#]"
  - "/main compiler option [C#]"
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# /main (C# Compiler Options)
このオプションは、**Main** メソッドを持つクラスが複数存在する場合に、プログラムのエントリ ポイントとして使用するクラスを指定します。  
  
## 構文  
  
```  
/main:class  
```  
  
## Arguments  
 `class`  
 **Main** メソッドを含む型。  
  
## 解説  
 [Main](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md) メソッドを持つ型を複数コンパイルする場合は、プログラムへのエントリ ポイントとして使用する **Main** メソッドをどの型が含んでいるかを指定できます。  
  
 このオプションは、.exe ファイルをコンパイルする場合に使用します。  
  
### Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **\[プロパティ\]** ページを開きます。  
  
2.  **\[アプリケーション\]** プロパティ ページをクリックします。  
  
3.  **\[スタートアップの設定\]** プロパティを変更します。  
  
     このコンパイラ オプションをコードから設定するには、「<xref:VSLangProj80.ProjectProperties3.StartupObject%2A>」を参照してください。  
  
## 使用例  
 `t2.cs` および `t3.cs` をコンパイルし、**Main** メソッドが `Test2` にあることを指定するには、次のコードを使用します。  
  
```  
csc t2.cs t3.cs /main:Test2  
```  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)