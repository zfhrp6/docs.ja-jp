---
title: "Type arguments could not be inferred from the delegate | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc36564"
  - "vbc36564"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36564"
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
caps.latest.revision: 5
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 5
---
# Type arguments could not be inferred from the delegate
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

代入ステートメントで `AddressOf` を使用して、ジェネリック プロシージャのアドレスをデリゲートに代入していますが、ジェネリック プロシージャに型引数が何も指定されていません。  
  
 通常、ジェネリック型を呼び出すときには、ジェネリック型に定義された各型パラメーターに型引数を指定します。  型引数を何も指定しなければ、コンパイラは型パラメーターに渡される型を推測しようとします。  コンパイラが型を推測するための十分な情報をコンテキストから得ることができない場合は、エラーが生成されます。  
  
 **エラー ID:** BC36564  
  
### このエラーを解決するには  
  
-   `AddressOf` 式の中で、ジェネリック プロシージャに型引数を指定します。  
  
## 参照  
 [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Generic Procedures in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)   
 [Type List](../../../visual-basic/language-reference/statements/type-list.md)   
 [拡張メソッド](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)