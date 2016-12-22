---
title: "#region (C# リファレンス) | Microsoft Docs"
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
  - "#region"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#region ディレクティブ [C#]"
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# #region (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`#region` を使用すると、コードのブロックを指定できます。このブロックは、Visual Studio コード エディターの[アウトライン](/visual-studio/ide/outlining)機能を使用して、展開や折りたたみができます。  コード ファイルが長い場合は、現在操作している部分に集中できるように 1 つ以上の領域を折りたたむ \(非表示にする\) ことができると便利です。  領域を定義する方法を次の例に示します。  
  
```  
  
      #region MyClass definition  
public class MyClass   
{  
    static void Main()   
    {  
    }  
}  
#endregion  
```  
  
## 解説  
 `#region` ブロックは、[\#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) ディレクティブで終了させる必要があります。  
  
 `#region` ブロックは、[\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ブロックとオーバーラップすることはできません。  ただし、`#region`ブロックを `#if` ブロック内に入れ子にしたり、`#if` ブロックを `#region` ブロック内に入れ子にしたりすることはできます。  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# プリプロセッサ ディレクティブ](../../../visual-basic/reference/command-line-compiler/index.md)