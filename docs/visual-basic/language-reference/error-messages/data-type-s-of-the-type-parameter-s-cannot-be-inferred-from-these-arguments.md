---
title: "Data type(s) of the type parameter(s) cannot be inferred from these arguments | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc36644"
  - "bc36647"
  - "vbc36647"
  - "vbc36644"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36644"
  - "BC36647"
ms.assetid: 0e0050f2-2039-4311-b260-f0ebfde84189
caps.latest.revision: 6
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 6
---
# Data type(s) of the type parameter(s) cannot be inferred from these arguments
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

型パラメーターのデータ型を、これらの引数から推論することはできません。データ型を明示的に指定すると、このエラーが修正される可能性があります。  
  
 このエラーは、オーバーロードの解決が失敗したときに発生します。  特定のオーバーロード候補が削除された理由を示す、従属メッセージとして発生します。  このエラー メッセージは、コンパイラが型の推論を使用して、型パラメーターのデータ型を見つけることができないということを説明しています。  
  
> [!NOTE]
>  引数を指定できない場合 \(たとえば、クエリ式内のクエリ演算子など\)、エラーの 2 つ目の文は表示されません。  
  
 エラーのコード例を次に示します。  
  
```vb#  
Module Module1  
  
    Sub Main()  
  
        '' Not Valid.  
        'OverloadedGenericMethod("Hello", "World")  
  
    End Sub  
  
    Sub OverloadedGenericMethod(Of T)(ByVal x As String,   
                                      ByVal y As InterfaceExample(Of T))  
    End Sub  
  
    Sub OverloadedGenericMethod(Of T, R)(ByVal x As T,   
                                         ByVal y As InterfaceExample(Of R))  
    End Sub  
  
End Module  
  
Interface InterfaceExample(Of T)  
End Interface  
```  
  
 **Error ID:** BC36647 および BC36644  
  
### このエラーを解決するには  
  
-   型の推論に依存することなく、型パラメーターのデータ型を指定できる場合があります。  
  
## 参照  
 [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)   
 [Generic Procedures in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)   
 [Type Conversions in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)