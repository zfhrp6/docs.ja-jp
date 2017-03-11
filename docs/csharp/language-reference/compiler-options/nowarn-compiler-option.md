---
title: "/nowarn (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/nowarn"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "nowarn compiler option [C#]"
  - "/nowarn compiler option [C#]"
  - "-nowarn compiler option [C#]"
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# /nowarn (C# Compiler Options)
**\/nowarn** オプションを使用すると、コンパイラからの警告が出力されないようにできます。  警告番号が複数ある場合は、コンマで区切ります。  
  
## 構文  
  
```  
/nowarn:number1[,number2,...]  
```  
  
## Arguments  
 `number1`, `number2`  
 コンパイラで表示しないようにする警告の番号  
  
## 解説  
 必要なのは、警告 ID の数値を指定することだけです。  たとえば、CS0028 を表示しない場合は、`/nowarn:28` と指定します。  
  
 コンパイラは、`/nowarn` に渡された警告番号のうち、以前のリリースで有効であり、今はコンパイラからは削除されている番号は無視します。  たとえば、CS0679 は、Visual Studio .NET 2002 のコンパイラでは有効でしたが、それ以降は削除されています。  
  
 `/nowarn` オプションでは、次の警告が表示されないようにすることはできません。  
  
-   Compiler Warning \(level 1\) CS2002  
  
-   Compiler Warning \(level 1\) CS2023  
  
-   Compiler Warning \(level 1\) CS2029  
  
### Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **\[プロパティ\]** ページを開きます。  詳細については、「[\[ビルド\] ページ \(プロジェクト デザイナー\) \(C\#\)](/visual-studio/ide/reference/build-page-project-designer-csharp)」を参照してください。  
  
2.  **\[ビルド\]** プロパティ ページをクリックします。  
  
3.  **\[警告の表示なし\]** プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.DelaySign%2A>」を参照してください。  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [C\# Compiler Errors](../../../csharp/language-reference/compiler-messages/index.md)