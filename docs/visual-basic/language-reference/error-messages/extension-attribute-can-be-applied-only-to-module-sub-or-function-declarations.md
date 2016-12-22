---
title: "&#39;Extension&#39; attribute can be applied only to &#39;Module&#39;, &#39;Sub&#39;, or &#39;Function&#39; declarations | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36550"
  - "vbc36550"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36550"
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Extension&#39; attribute can be applied only to &#39;Module&#39;, &#39;Sub&#39;, or &#39;Function&#39; declarations
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Visual Basic でデータ型を拡張する唯一の方法は、標準モジュールの中に拡張メソッドを定義することです。  拡張メソッドは、`Sub` プロシージャでも `Function` プロシージャでもかまいません。  すべての拡張メソッドは、<xref:System.Runtime.CompilerServices?displayProperty=fullName> 名前空間の拡張属性 `<Extension()>` でマークする必要があります。  オプションとして、拡張メソッドを含むモジュールを、同じ方法でマークできます。  これ以外の拡張属性の使い方は無効です。  
  
 **エラー ID:** BC36550  
  
### このエラーを解決するには  
  
-   拡張属性を削除します。  
  
-   拡張機能を、モジュール内に定義されるメソッドとして再デザインします。  
  
## 使用例  
 `String` データ型の `Print` メソッドを定義する例を次に示します。  
  
```  
Imports StringUtility  
Imports System.Runtime.CompilerServices  
Namespace StringUtility  
    <Extension()>   
    Module StringExtensions  
        <Extension()>   
        Public Sub Print (ByVal str As String)  
            Console.WriteLine(str)  
        End Sub  
    End Module  
End Namespace  
  
```  
  
## 参照  
 [属性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)   
 [拡張メソッド](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)   
 [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)