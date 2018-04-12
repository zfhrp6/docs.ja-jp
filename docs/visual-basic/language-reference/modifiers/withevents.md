---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 68a58fd130c04f2ed0cb1f2e5b9250f6c85f120d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
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
