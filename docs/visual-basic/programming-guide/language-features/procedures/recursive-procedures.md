---
title: "再帰プロシージャ (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, procedures
- procedures, that call themselves
- procedures, recursive
- procedures, calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
caps.latest.revision: 13
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9fc95cd5f7cfd5637f6282c6ef571eb81bac1816
ms.lasthandoff: 03/13/2017

---
# <a name="recursive-procedures-visual-basic"></a>再帰プロシージャ (Visual Basic)
A*再帰*手順は、自分自身を呼び出します。 一般に、これは最も効果的な方法を記述する[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コードです。  
  
 次の手順では、再帰を使用して、元の引数の階乗を計算します。  
  
 [!code-vb[VbVbcnProcedures&51;](./codesnippet/VisualBasic/recursive-procedures_1.vb)]  
  
## <a name="considerations-with-recursive-procedures"></a>再帰プロシージャに関する考慮事項  
 **制限条件**します。 再帰を終了するには、少なくとも&1; つの条件をテストする再帰的な手順を設計する必要があり、再帰呼び出しの適切な数値の中でこのような条件が満たされるないケースを行う必要があります。 失敗せずに満たすことのできる、少なくとも&1; つの条件がない、プロシージャは、無限ループで実行するリスクが高くを実行します。  
  
 **メモリ使用量**します。 アプリケーションでは、ローカル変数の領域量が制限を持ちます。 プロシージャが自分自身を呼び出すたびに、ローカル変数の追加のコピーの領域を使用します。 最終的と、この処理がいつまでも続く場合、<xref:System.StackOverflowException>エラー</xref:System.StackOverflowException> 。  
  
 **効率性**します。 ほとんどの場合、再帰はループを置換できます。 ループには、引数の受け渡し、追加のストレージを初期化し、値を返すのオーバーヘッドはありません。 パフォーマンスは、再帰呼び出しなしの方があります。  
  
 **相互再帰**します。 2 つの手順では、互いを呼び出す場合は、パフォーマンスが大きく低下または無限ループではあってを監視することがあります。 このような設計は、1 つの再帰プロシージャと同じ問題を提示しますが、検出およびデバッグが困難になることができます。  
  
 **かっこを使った呼び出し**します。 ときに、`Function`プロシージャを呼び出す再帰的に、引数リストがない場合でも、かっこを付けて、プロシージャ名を従う必要があります。 関数名を取得する場合は、関数の戻り値を表しているとします。  
  
 **テスト**します。 再帰プロシージャを記述する場合に、非常に慎重に常にいくつかの制限の条件を満たしているかどうかを確認するテスト必要があります。 多すぎるの再帰呼び出しのためのメモリ不足が実行できないということを確認する必要があります。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.StackOverflowException></xref:System.StackOverflowException>   
 [手順](./index.md)   
 [Sub プロシージャ](./sub-procedures.md)   
 [Function プロシージャ](./function-procedures.md)   
 [プロパティ プロシージャ](./property-procedures.md)   
 [演算子プロシージャ](./operator-procedures.md)   
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)   
 [プロシージャのオーバー ロード](./procedure-overloading.md)   
 [トラブルシューティングの手順](./troubleshooting-procedures.md)   
 [ループ構造](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [例外のトラブルシューティング : System.StackOverflowException](http://msdn.microsoft.com/library/51b71217-c507-4f5b-bc35-0236180d7968)
