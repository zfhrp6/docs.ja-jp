---
title: "構造体 (Visual Basic) の意思決定 |Microsoft ドキュメント"
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
- statements [Visual Basic], control flow
- If statement, decision structures
- If statement, If...Then...Else
- control flow, decision structures
- decision structures
- conditional statements, decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
caps.latest.revision: 29
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: c69b487322dc75ae8d54f42c1c62f8f5cc35757d
ms.lasthandoff: 03/13/2017

---
# <a name="decision-structures-visual-basic"></a>条件判断構造 (Visual Basic)
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]条件をテストし、そのテストの結果に応じて別の操作を実行することができます。 True または false の場合、さまざまな値の式、または一連のステートメントを実行するときに生成された例外のさまざまな条件をテストできます。  
  
 次の図は、条件が真かをテストし、true または false であるかに基づいて異なる処理を実行する条件判断構造を示しています。  
  
 ![If のフロー チャート.そうしたら。。。Else 構文](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse")  
条件が true と false の場合は、異なる処理を実行  
  
## <a name="ifthenelse-construction"></a>もし。。。そうしたら。。。Else 構文  
 `If...Then...Else`構造では、1 つまたは複数の条件をテストして、各条件に応じて&1; つまたは複数のステートメントを実行できます。 条件をテストし、次の方法で行うことができます。  
  
-   条件の場合は、1 つまたは複数のステートメントを実行します。`True`  
  
-   条件の場合は、1 つまたは複数のステートメントを実行します。`False`  
  
-   条件の場合は、いくつかのステートメントを実行`True`およびその他のユーザーである場合`False`  
  
-   前の条件の場合、追加的な条件をテストします。`False`  
  
 これらすべての可能性を提供する制御構造体は、[場合.そうしたら。。。Else ステートメント](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)します。 1 つのテストと&1; つのステートメントを実行する必要がある場合は、単一行のバージョンを使用できます。 条件とアクションのより複雑なセットがある場合は、複数行のバージョンを使用することができます。  
  
## <a name="selectcase-construction"></a>選択してください。Case 構造  
 `Select...Case`構築では、1 回式を評価し、異なる一連の別の使用可能な値に基づくステートメントを実行することができます。 詳細については、次を参照してください[を選択しています.。Case ステートメント](../../../../visual-basic/language-reference/statements/select-case-statement.md)します。  
  
## <a name="trycatchfinally-construction"></a>しようとしてください.キャッチしてください.最後に構築  
 `Try...Catch...Finally`構造では、一連のステートメントのいずれかの例外が発生した場合は、コントロールを保持する環境の下のステートメントを実行できます。 さまざまな例外のさまざまなアクションを実行できます。 全体を終了する前に実行されるコードのブロックを指定することもできます。`Try...Catch...Finally`どうなるかに関係なく、構築します。 詳細については、次を参照してください[しようとしています.。キャッチしてください.Finally ステートメント](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)します。  
  
> [!NOTE]
>  多くの制御構造のキーワードをクリックすると、すべての構造のキーワードが強調表示されます。 クリックすると、`If`で、`If...Then...Else`構築のすべてのインスタンス`If`、 `Then`、 `ElseIf`、 `Else`、および`End If`構造で強調表示されます。 前または次の強調表示されているキーワードに移動するには、ctrl キーと shift キーを押しながら下方向キーまたは ctrl キーと shift キーを押しながら上方向をキーを押します。  
  
## <a name="see-also"></a>関連項目  
 [制御フロー](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [ループ構造](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [他の制御構造](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)   
 [入れ子になった制御構造](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [If 演算子](../../../../visual-basic/language-reference/operators/if-operator.md)
