---
title: "#pragma 警告 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "#pragma warning"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#pragma warning [C#]"
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# #pragma 警告 (C# リファレンス)
`#pragma warning` を使用すると、特定の警告を有効または無効にできます。  
  
## 構文  
  
```  
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
#### パラメーター  
 `warning-list`  
 コンマで区切られた警告番号の一覧。  "CS" プレフィックスを付けず、番号だけを入力します。  
  
 警告番号を指定しないと、`disable` ではすべての警告が無効になり、`restore` ではすべての警告が有効になります。  
  
> [!NOTE]
>  Visual Studio で警告番号を見つけるには、プロジェクトをビルドし、**\[出力\]** ウィンドウで警告番号を検索します。  
  
## 使用例  
  
```  
// pragma_warning.cs  
using System;  
  
#pragma warning disable 414, 3021  
[CLSCompliant(false)]  
public class C  
{  
    int i = 1;  
    static void Main()  
    {  
    }  
}  
#pragma warning restore 3021  
[CLSCompliant(false)]  // CS3021  
public class D  
{  
    int i = 1;  
    public static void F()  
    {  
    }  
}  
```  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# プリプロセッサ ディレクティブ](../../../csharp/language-reference/preprocessor-directives/index.md)   
 [C\# Compiler Errors](../../../csharp/language-reference/compiler-messages/index.md)