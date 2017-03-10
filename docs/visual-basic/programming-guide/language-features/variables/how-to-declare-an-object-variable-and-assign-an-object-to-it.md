---
title: "How to: Declare an Object Variable and Assign an Object to It in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "object variables, declaring"
  - "declaring object variables"
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# How to: Declare an Object Variable and Assign an Object to It in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) の変数は、[Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) で `As Object` を指定して宣言します。  このような変数にオブジェクトを代入するには、代入ステートメントまたは初期化処理句で等号 \(`=`\) の右側にオブジェクトを配置します。  
  
## 使用例  
 次の例では、`Object` 変数を宣言し、現在のインスタンスを代入します。  
  
```  
  
      Dim thisObject As Object  
thisObject = "This is an Object"  
```  
  
 宣言の一部として変数を初期化することによって、宣言と代入を結合できます。  次の例は、上の例と同じ意味です。  
  
```  
Dim thisObject As Object = "This is an Object"  
```  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   <xref:System> 名前空間への参照  
  
-   `Dim` ステートメントを記述するクラス、構造、またはモジュール  
  
-   代入ステートメントを記述するプロシージャ  
  
## 参照  
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)