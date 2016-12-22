---
title: "AddressOf Operator (Visual Basic) | Microsoft Docs"
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
  - "AddressOf"
  - "vb.AddressOf"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "AddressOf operator"
  - "addresses, passing to API procedures"
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# AddressOf Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

特定のプロシージャを参照するプロシージャ デリゲート インスタンスを作成します。  
  
## 構文  
  
```  
  
AddressOf procedurename  
```  
  
## 指定項目  
 `procedurename`  
 必ず指定します。  新しく作成されたプロシージャ デリゲートによって参照されるプロシージャを指定します。  
  
## 解説  
 `AddressOf` 演算子により、`procedurename` で指定された関数を参照する関数デリゲートが作成されます。  指定されたプロシージャがインスタンス メソッドである場合、関数デリゲートはインスタンスとメソッドの両方を参照します。  その後、関数デリゲートが呼び出されると、指定されたインスタンスの指定されたメソッドが呼び出されます。  
  
 `AddressOf` 演算子は、デリゲート コンストラクターのオペランドとして使用できます。また、デリゲートの種類をコンパイラで決定できる状況で使用できます。  
  
## 使用例  
 `AddressOf` 演算子を使って、ボタンの `Click` イベントを処理するデリゲートを指定する例を次に示します。  
  
 [!code-vb[VbVbalrDelegates#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]  
  
## 使用例  
 `AddressOf` 演算子を使用して、スレッドの起動関数を指定する例を次に示します。  
  
 [!code-vb[VbVbalrDelegates#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]  
  
## 参照  
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Delegates](../../../visual-basic/programming-guide/language-features/delegates/delegates.md)