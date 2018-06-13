---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 240058a534456ae20c9c129a068bae575ac45eda
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33596009"
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
イベントを発生させるクラスのインスタンスを 1 つまたは複数の宣言されたメンバー変数が参照しているを指定します。  
  
## <a name="remarks"></a>コメント  
 使用して変数を定義するとき`WithEvents`、メソッドを使用して、変数のイベントを処理する宣言によって指定できます、`Handles`キーワード。  
  
 使用することができます`WithEvents`クラスまたはモジュール レベルでのみです。 つまりの宣言コンテキスト、`WithEvents`変数がクラスまたはモジュールにある必要があるあり、ソース ファイル、名前空間、構造体、またはプロシージャにすることはできません。  
  
 使用することはできません`WithEvents`構造体のメンバーにします。  
  
 それぞれの変数を宣言することができます: 配列でない — で`WithEvents`です。  
  
## <a name="rules"></a>ルール  
  
-   **要素の型。** 宣言する必要があります`WithEvents`オブジェクト変数を使用できるように変数クラスのインスタンス。 ただし、そのままは宣言できません`Object`です。 それは、イベントを発生させる特定のクラスとして宣言する必要があります。  
  
 `WithEvents`修飾子は、このコンテキストで使用できます: [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>関連項目  
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)  
 [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)
