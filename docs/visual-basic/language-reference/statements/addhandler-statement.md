---
title: AddHandler ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: db8131dc82aed40e725c9375efef274fb6917d41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="addhandler-statement"></a>AddHandler ステートメント
実行時にイベントをイベント ハンドラーに関連付けます。  
  
## <a name="syntax"></a>構文  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>指定項目  
 `event`  
 処理するイベントの名前。  
  
 `eventhandler`  
 イベントを処理するプロシージャの名前。  
  
## <a name="remarks"></a>コメント  
 `AddHandler`と`RemoveHandler`ステートメントでは、開始およびプログラムの実行中にいつでもイベントの処理を停止することができます。  
  
 署名、`eventhandler`プロシージャは、イベントのシグネチャと一致する必要があります`event`です。  
  
 `Handles` キーワードと `AddHandler` ステートメントはどちらも特定のプロシージャで特定のイベントを処理するように指定できますが、両者には違いがあります。 `AddHandler` ステートメントは、実行時にプロシージャをイベントに接続します。 `Handles` キーワードは、プロシージャの定義時に特定のイベントを処理するよう指定する場合に使用します。 詳細については、次を参照してください。[処理](../../../visual-basic/language-reference/statements/handles-clause.md)です。  
  
> [!NOTE]
>  カスタム イベントの場合、`AddHandler`ステートメントには、イベントが呼び出される`AddHandler`アクセサー。 カスタム イベントの詳細については、次を参照してください。 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)です。  
  
## <a name="example"></a>例  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [RemoveHandler ステートメント](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)  
 [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)
