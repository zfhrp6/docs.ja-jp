---
title: "AddHandler ステートメント |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
dev_langs:
- VB
helpviewer_keywords:
- AddHandler statement
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
caps.latest.revision: 15
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
ms.openlocfilehash: 728d8393c44d777f9cc016d9cf66030036582ae4
ms.lasthandoff: 03/13/2017

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
 `AddHandler`と`RemoveHandler`ステートメントを使用すると、起動して、プログラムの実行中にいつでもイベント処理を停止します。  
  
 署名、`eventhandler`プロシージャは、イベントのシグネチャと一致する必要があります`event`します。  
  
 `Handles` キーワードと `AddHandler` ステートメントはどちらも特定のプロシージャで特定のイベントを処理するように指定できますが、両者には違いがあります。 `AddHandler` ステートメントは、実行時にプロシージャをイベントに接続します。 `Handles` キーワードは、プロシージャの定義時に特定のイベントを処理するよう指定する場合に使用します。 詳細については、次を参照してください。[処理](../../../visual-basic/language-reference/statements/handles-clause.md)します。  
  
> [!NOTE]
>  カスタム イベントの場合、`AddHandler`ステートメントで呼び出されるイベントの`AddHandler`アクセサー。 カスタム イベントの詳細については、次を参照してください。 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)します。  
  
## <a name="example"></a>例  
 [!code-vb[VbVbalrEvents&17;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [RemoveHandler ステートメント](../../../visual-basic/language-reference/statements/removehandler-statement.md)   
 [ハンドル](../../../visual-basic/language-reference/statements/handles-clause.md)   
 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)   
 [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)
