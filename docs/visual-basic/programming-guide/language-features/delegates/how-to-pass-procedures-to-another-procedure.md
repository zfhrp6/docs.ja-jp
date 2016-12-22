---
title: "How to: Pass Procedures to Another Procedure in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "AddressOf operator"
  - "delegates [Visual Basic], passing procedures"
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Pass Procedures to Another Procedure in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

この例では、プロシージャを他のプロシージャに渡すためにデリゲートを使用する方法について説明します。  
  
 デリゲートは、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] の他の型と同様に使用できる型です。  `AddressOf` 演算子は、プロシージャ名に適用される場合、デリゲート オブジェクトを返します。  
  
 この例には、`AddressOf` 演算子を指定して取得した他のプロシージャへの参照を取得できるデリゲート パラメーターを使ったプロシージャが含まれています。  
  
### デリゲートおよび一致プロシージャの作成  
  
1.  `MathOperator` という名前のデリゲートを作成する  
  
     [!code-vb[VbVbalrDelegates#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_1.vb)]  
  
2.  `MathOperator` と一致するパラメーターと戻り値を持つ `AddNumbers` という名前のプロシージャを、シグネチャが一致するように作成します。  
  
     [!code-vb[VbVbalrDelegates#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_2.vb)]  
  
3.  `MathOperator` と一致するシグネチャを持つ `SubtractNumbers` という名前のプロシージャを作成します。  
  
     [!code-vb[VbVbalrDelegates#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_3.vb)]  
  
4.  パラメーターとしてデリゲートを取得する `DelegateTest` という名前のプロシージャを作成します。  
  
     このプロシージャは、`AddNumbers` または `SubtractNumbers` のシグネチャを受け入れることができます。これらのシグネチャは、`MathOperator` のシグネチャと一致するためです。  
  
     [!code-vb[VbVbalrDelegates#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_4.vb)]  
  
5.  パラメーターとして `AddNumbers` に対するデリゲートを指定し、再びパラメーターとして `SubtractNumbers` へのデリゲートが指定された `DelegateTest` を一度呼び出す `Test` という名前のプロシージャを作成します。  
  
     [!code-vb[VbVbalrDelegates#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_5.vb)]  
  
     `Test` が呼び出されると、まず、`5` と `3` に対して実行された `AddNumbers` の結果が表示されます。これは 8 になります。  次に、`9` と `3` に対して実行された `SubtractNumbers` の結果が表示されます。これは 6 になります。  
  
## 参照  
 [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [AddressOf Operator](../../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Delegate Statement](../../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [How to: Invoke a Delegate Method](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)