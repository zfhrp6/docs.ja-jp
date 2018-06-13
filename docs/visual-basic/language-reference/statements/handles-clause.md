---
title: Handles 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: 15ce6a25aa5f403a2e55beb57b3693095743e52f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603718"
---
# <a name="handles-clause-visual-basic"></a>Handles 句 (Visual Basic)
プロシージャが指定されたイベントを処理することを宣言します。  
  
## <a name="syntax"></a>構文  
  
```  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a>指定項目  
 `proceduredeclaration`  
 イベントを処理するプロシージャの `Sub` プロシージャ宣言。  
  
 `eventlist`  
 コンマで区切られた、`proceduredeclaration` が処理するイベントの一覧。 イベントは、現在のクラスの基底クラス、または `WithEvents` キーワードを使用して宣言されたオブジェクトによって発生する必要があります。  
  
## <a name="remarks"></a>コメント  
 プロシージャ宣言の最後で `Handles` キーワードを使用すると、 `WithEvents` キーワードで宣言されたオブジェクト変数によって発生したイベントが処理されるようになります。 また、`Handles` キーワードを派生クラスで使用すると、基底クラスからのイベントを処理することもできます。  
  
 `Handles` キーワードと `AddHandler` ステートメントはどちらも特定のプロシージャで特定のイベントを処理するように指定できますが、両者には違いがあります。 `Handles` キーワードは、プロシージャの定義時に特定のイベントを処理するよう指定する場合に使用します。 `AddHandler` ステートメントは、実行時にプロシージャをイベントに接続します。 詳細については、次を参照してください。 [AddHandler ステートメント](../../../visual-basic/language-reference/statements/addhandler-statement.md)です。  
  
 カスタム イベントの場合、アプリケーションは、プロシージャをイベント ハンドラーとして追加するときにイベントの `AddHandler` アクセサーを呼び出します。 カスタム イベントの詳細については、次を参照してください。 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)です。  
  
## <a name="example"></a>例  
 [!code-vb[VbVbalrEvents#2](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_1.vb)]  
  
 派生クラスで `Handles` ステートメントを使用して基底クラスからのイベントを処理する方法を次の例に示します。  
  
 [!code-vb[VbVbalrEvents#3](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_2.vb)]  
  
## <a name="example"></a>例  
 次の例には 2 つのボタン イベント ハンドラーが含まれています、 **WPF アプリケーション**プロジェクト。  
  
 [!code-vb[VbVbalrEvents#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_3.vb)]  
  
## <a name="example"></a>例  
 次の例は、前の例と同じです。 `Handles` 句の `eventlist` には 2 つのボタンのイベントが含まれています。  
  
 [!code-vb[VbVbalrEvents#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_4.vb)]  
  
## <a name="see-also"></a>関連項目  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)  
 [AddHandler ステートメント](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [RemoveHandler ステートメント](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)  
 [RaiseEvent ステートメント](../../../visual-basic/language-reference/statements/raiseevent-statement.md)  
 [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)
