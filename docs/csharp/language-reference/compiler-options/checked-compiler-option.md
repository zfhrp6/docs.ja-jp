---
title: "/checked (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/checked"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "checked compiler option [C#]"
  - "-checked compiler option [C#]"
  - "/checked compiler option [C#]"
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /checked (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

**\/checked** オプションは、結果がデータ型の範囲外の値になる、および [checked](../../../csharp/language-reference/keywords/checked.md) キーワードまたは [unchecked](../../../csharp/language-reference/keywords/unchecked.md) キーワードのスコープ外にある整数算術演算ステートメントによって、実行時に例外を発生させるかどうかを指定します。  
  
## 構文  
  
```  
/checked[+ | -]  
```  
  
## 解説  
 `checked` キーワードまたは `unchecked` キーワードのスコープ内にある整数算術演算ステートメントは、**\/checked** オプションの影響を受けません。  
  
 `checked` キーワードまたは `unchecked` キーワードのスコープ外にある整数算術演算ステートメントの結果がデータ型の範囲外の値になる場合、コンパイル時に **\/checked\+** \(**\/checked**\) オプションを指定すると、そのステートメントによって実行時に例外が発生します。  コンパイル時に **\/checked\-** が使用された場合、そのステートメントによって実行時に例外は発生しません。  
  
 このオプションの既定値は **\/checked\-** です。  **\/checked\-** を使用する場面としては、大規模なアプリケーションのビルドがあります。  このようなアプリケーションのビルドでは、自動化ツールが使用されることがあり、そのツールで **\/checked** が自動的に \+ に設定される場合があります。  **\/checked\-** を指定することによって、ツールのグローバルな既定値をオーバーライドできます。  
  
### Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **\[プロパティ\]** ページを開きます。  詳細については、「[\[ビルド\] ページ \(プロジェクト デザイナー\) \(C\#\)](../Topic/Build%20Page,%20Project%20Designer%20\(C%23\).md)」を参照してください。  
  
2.  **\[ビルド\]** プロパティ ページをクリックします。  
  
3.  \[詳細設定\] ボタンをクリックします。  
  
4.  **\[演算のオーバーフローおよびアンダーフローのチェック\]** プロパティを変更します。  
  
 プログラムによってこのコンパイラ オプションにアクセスする方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>」を参照してください。  
  
## 使用例  
 次のコマンドにより、`t2.cs` がコンパイルされます。  コマンドで `/checked` を使用すると、`checked` キーワードまたは `unchecked` キーワードのスコープ外にある、および結果がデータ型の範囲外の値になるファイル内の整数算術演算ステートメントによって、実行時に例外を発生させるように指定されます。  
  
```  
csc t2.cs /checked  
```  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [Introduction to the Project Designer](http://msdn.microsoft.com/ja-jp/898dd854-c98d-430c-ba1b-a913ce3c73d7)