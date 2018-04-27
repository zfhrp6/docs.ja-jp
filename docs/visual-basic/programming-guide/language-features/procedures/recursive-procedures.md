---
title: 再帰プロシージャ (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 471746f4412b61c9782e8019aa8a9ec6221afb04
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="recursive-procedures-visual-basic"></a>再帰プロシージャ (Visual Basic)
A*再帰*手順は、自分自身を呼び出します。 通常、これは Visual Basic コードを記述する最も効果的な方法ではありません。  
  
 次の手順では、元の引数の階乗を計算するのに再帰を使用します。  
  
 [!code-vb[VbVbcnProcedures#51](./codesnippet/VisualBasic/recursive-procedures_1.vb)]  
  
## <a name="considerations-with-recursive-procedures"></a>再帰プロシージャに関する考慮事項  
 **制限条件**です。 再帰を終了するには、少なくとも 1 つの条件をテストする再帰的な手順を設計する必要がありも、再帰呼び出しの適切な数値の中でこのような条件が満たされるないケースを処理する必要があります。 失敗することがなく満たすことのできるに少なくとも 1 つの条件が、存在しない、プロシージャには、無限ループを実行する危険度の高いが実行されます。  
  
 **メモリ使用状況**。 アプリケーションは、限られた量のローカル変数の領域を持ちます。 プロシージャが、それ自体を呼び出すたびに、ローカル変数の追加のコピーの領域を使用します。 最終的と、このプロセスが無期限に解決しない場合は、<xref:System.StackOverflowException>エラーです。  
  
 **効率**です。 ほとんどの場合、再帰はループを置換できます。 ループには、引数の渡し、追加のストレージを初期化し、値を返すことのオーバーヘッドはありません。 パフォーマンスは、再帰呼び出しなしの方があります。  
  
 **相互再帰**です。 2 つの手順では、互いを呼び出す場合、パフォーマンスが大きく低下または無限ループを確認する場合があります。 この設計では、1 つの再帰プロシージャと同じ問題を表示しますが検出およびデバッグが困難になることができます。  
  
 **かっこで呼び出して**です。 ときに、`Function`プロシージャを呼び出す自体を再帰的に、引数リストがない場合でも、プロシージャ名をかっこを行う必要があります。 それ以外の場合、関数名が取得された関数の戻り値を表しているとします。  
  
 **テスト**です。 再帰的なプロシージャを記述する場合はテストする非常に慎重に常にいくつかの制限の条件を満たしているかどうかを確認します。 再帰呼び出しが多すぎるためのメモリが不足して実行できないことを確認する必要があります。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.StackOverflowException>  
 [手順](./index.md)  
 [Sub プロシージャ](./sub-procedures.md)  
 [Function プロシージャ](./function-procedures.md)  
 [Property プロシージャ](./property-procedures.md)  
 [演算子プロシージャ](./operator-procedures.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [プロシージャのオーバーロード](./procedure-overloading.md)  
 [プロシージャのトラブルシューティング](./troubleshooting-procedures.md)  
 [ループ構造](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [例外のトラブルシューティング : System.StackOverflowException](http://msdn.microsoft.com/library/51b71217-c507-4f5b-bc35-0236180d7968)
