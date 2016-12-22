---
title: "Recursive Procedures (Visual Basic) | Microsoft Docs"
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
  - "Visual Basic code, procedures"
  - "procedures, that call themselves"
  - "procedures, recursive"
  - "procedures, calling"
  - "recursive procedures"
  - "functions [Visual Basic], calling recursively"
  - "recursion"
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Recursive Procedures (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

*再帰*プロシージャとは、自分自身を呼び出すプロシージャです。  一般的に、これは [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] コード作成方法として効率的ではありません。  
  
 次のプロシージャは、再帰を使って元の引数の階乗を計算します。  
  
 [!code-vb[VbVbcnProcedures#51](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/recursive-procedures_1.vb)]  
  
## 再帰プロシージャの考慮事項  
 **制限条件**。  再帰プロシージャでは、再帰を終了する条件を最低 1 つテストする必要があります。また、妥当な回数の再帰呼び出しを行ってもこの条件が満たされない場合の処理も必要です。  必ず満たされる条件を最低 1 つ用意しないと、プロシージャが無限ループに陥る可能性が高くなります。  
  
 **メモリ使用状況**。  アプリケーションがローカル変数に使用できる領域は限られています。  プロシージャが自分自身を呼び出す際、ローカル変数のコピーが毎回作成され、領域を消費します。  このプロセスがいつまでも続くと、最終的には <xref:System.StackOverflowException> エラーが発生します。  
  
 **効率**。  ほとんどの場合、再帰はループで代替できます。  ループでは引数を渡したり、追加の領域を初期化したり、値を返したりするオーバーヘッドは発生しません。  再帰呼び出しを使用しないほうが、パフォーマンスは大きく向上します。  
  
 **相互再帰**。  2 つのプロシージャがお互いを呼び出すと、パフォーマンスが大きく低下したり、無限ループが発生したりします。  このようなデザインでは、単独の再帰プロシージャと同じ問題が発生しますが、検出とデバッグはずっと困難です。  
  
 **かっこを使った呼び出し**。  `Function` プロシージャを再帰的に呼び出すときには、引数リストがない場合でも、プロシージャ名の後にかっこを付ける必要があります。  そうしないと、関数名が関数の戻り値を表していると見なされてしまいます。  
  
 **テスト**。  再帰プロシージャを作成した場合、最低 1 つの制限条件を満たしていることを必ずテストする必要があります。  また、再帰呼び出しが多すぎるためにメモリを使い果たすことがないことを確認する必要があります。  
  
## 参照  
 <xref:System.StackOverflowException>   
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Function プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Property プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Troubleshooting Procedures](../../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [例外のトラブルシューティング : System.StackOverflowException](../Topic/Troubleshooting%20Exceptions:%20System.StackOverflowException.md)