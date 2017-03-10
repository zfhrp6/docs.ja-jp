---
title: "Implicit conversion from &#39;&lt;typename1&gt;&#39; to &#39;&lt;typename2&gt;&#39; in copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument. | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc41999"
  - "bc41999"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC41999"
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# Implicit conversion from &#39;&lt;typename1&gt;&#39; to &#39;&lt;typename2&gt;&#39; in copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument.
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プロシージャの呼び出しに指定された [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) 引数の型が、それに対応するパラメーターの型と異なります。  
  
 引数を `ByRef` で渡した場合に、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は参照を渡すのではなく、引数の値をプロシージャのローカル変数にコピーする場合があります。  このようなケースでは、プロシージャから制御が戻ったとき、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] はローカル変数の値を呼び出し元のコードの引数にコピーして戻す必要があります。  
  
 `ByRef` の引数の値がプロシージャにコピーされるとき、引数とパラメーターの型が同じであれば、変換は必要ありません。  しかし、型が異なる場合、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は、双方向で変換を実行する必要があります。  `CType` またはその他の変換キーワードをプロシージャの引数またはパラメーターで使うことはできないため、このような変換は常に暗黙の変換となります。  
  
 既定では、このメッセージは警告です。  警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、[Visual Basic での警告の構成](/visual-studio/ide/configuring-warnings-in-visual-basic) を参照してください。  
  
 **Error ID:** BC41999  
  
### このエラーを解決するには  
  
-   可能であれば、呼び出し元の引数にプロシージャのパラメーターと同じ型を使用します。そうすれば、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は変換を行う必要がありません。  
  
-   パラメーターの型と異なる型の引数を指定してプロシージャを呼び出す必要があるが、値を呼び出し元の引数に戻す必要がない場合は、パラメーターを `ByRef` ではなく [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) で定義します。  
  
## 参照  
 [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Passing Arguments by Value and by Reference](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)