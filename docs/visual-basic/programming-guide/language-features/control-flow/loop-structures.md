---
title: "ループ構造 (Visual Basic) |Microsoft ドキュメント"
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
- control flow, loops
- For keyword [Visual Basic], loop structures
- loops
- loop structures
- statements [Visual Basic], loop
- Do statement, Do loops
- conditional statements, loop structures
ms.assetid: ecacb09b-a4c9-42be-98b2-a15d368b5db8
caps.latest.revision: 18
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
ms.openlocfilehash: c2835b9d9d22196447fb1863f6e4fa9bd11ecf0a
ms.lasthandoff: 03/13/2017

---
# <a name="loop-structures-visual-basic"></a>ループ構造 (Visual Basic)
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]ループ構造を使用すると、1 つまたは複数の行のコードを繰り返し実行できます。 条件になるまで、ループ構造内のステートメントを繰り返すことができます`True`条件になるまで、`False`コレクションの回数、または各要素に対して&1; 回の番号を指定します。  
  
 次の図は、条件が true になるまでは、一連のステートメントを実行するループ構造を示しています。  
  
 ![フロー チャート.ループ](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")  
条件が true になるまで、一連のステートメントを実行しています。  
  
## <a name="while-loops"></a>While ループ  
 The `While`...`End While`構築には一連のステートメントが実行される、条件で指定されている限り、`While`ステートメントは`True`です。 詳細については、次を参照してください[中.。While ステートメント終了](../../../../visual-basic/language-reference/statements/while-end-while-statement.md)します。  
  
## <a name="do-loops"></a>Do ループ  
 The `Do`...`Loop`構築では、先頭またはループ構造の末尾のいずれかの条件をテストすることができます。 条件がある限り、ループ処理を実行するかどうかを指定することも`True`になるまで`True`します。 詳細については、次を参照してください[操作を行います.。ステートメントのループ](../../../../visual-basic/language-reference/statements/do-loop-statement.md)します。  
  
## <a name="for-loops"></a>For ループ  
 The `For`...`Next`構築は、指定された回数だけループを実行します。 呼ばれますループ制御変数を使用して、*カウンター*繰り返しを追跡するためです。 開始と終了日、このカウンターの値を指定して、必要に応じて、量が増加している&1; 回の繰り返しから次の手順を指定することができます。 詳細については、次を参照してください[にしています.。次のステートメントの](../../../../visual-basic/language-reference/statements/for-next-statement.md)です。  
  
## <a name="for-each-loops"></a>For Each ループ  
 The `For Each`...`Next`構築は、コレクション内の各要素に対して&1; 回のステートメントのセットを実行します。 ループ制御変数を指定するが、開始または終了値を確認する必要はありません。 詳細については、次を参照してください[ごとにしています.。次のステートメントの](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)です。  
  
## <a name="see-also"></a>関連項目  
 [制御フロー](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [条件判断構造](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)   
 [他の制御構造](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)   
 [入れ子になった制御構造](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
