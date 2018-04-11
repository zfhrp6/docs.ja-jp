---
title: Static (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e08f46076281e766a5bc0b99cd61fee9cd41ece5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="static-visual-basic"></a>Static (Visual Basic)
1 つまたは複数の宣言されたローカル変数を引き続き存在し、宣言されているプロシージャの終了後、最新の値を保持するように指定します。  
  
## <a name="remarks"></a>コメント  
 通常、プロシージャ内のローカル変数は、プロシージャは停止すると、すぐに存在しなくなります。 静的変数存在し、続け、最新の値を保持します。 コード、プロシージャを呼び出します。 次には、変数が再初期化されていないに割り当てられている最新の値をそのまま保持します。 静的変数で定義されているクラスまたはモジュールの有効期間中に存在し続けます。  
  
## <a name="rules"></a>ルール  
  
-   **宣言コンテキスト。** 使用することができます`Static`ローカル変数に対してのみです。 つまりの宣言コンテキスト、`Static`変数は、プロシージャまたはプロシージャでは、ブロックに指定する必要があり、ソース ファイル、名前空間、クラス、構造体、またはモジュールにすることはできません。  
  
     使用することはできません`Static`プロシージャの内部で構造体。  
  
-   データ型`Static`ローカル変数を推論することはできません。 詳細については、次を参照してください。[ローカル型推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)です。  
  
-   **結合された修飾子。** 指定することはできません`Static`と共に`ReadOnly`、 `Shadows`、または`Shared`同じ宣言内で。  
  
## <a name="behavior"></a>動作  
 静的変数を宣言する場合、`Shared`プロシージャ、静的変数の 1 つだけのコピーは、アプリケーション全体の使用。 呼び出す、`Shared`クラスを使用してプロシージャ名、変数、クラスのインスタンスを指すではなくです。  
  
 ないプロシージャ内で静的変数を宣言する場合`Shared`変数の 1 つのコピーはクラスの各インスタンスの使用のみ。 クラスの特定のインスタンスが指す変数を使用して、非共有プロシージャを呼び出します。  
  
## <a name="example"></a>例  
 次の例は、`Static` の使い方を示しています。  
  
 [!code-vb[VbVbalrKeywords#5](../../../visual-basic/language-reference/codesnippet/VisualBasic/static_1.vb)]  
  
 `Static`変数`totalSales`1 つだけの時間は 0 に初期化します。 入力するたびに`updateSales`、`totalSales`まだを計算した最新の値。  
  
 `Static`修飾子は、このコンテキストで使用できます。  
  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>関連項目  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)  
 [Visual Basic における有効期間](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [変数宣言](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [構造体](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [ローカル型の推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
