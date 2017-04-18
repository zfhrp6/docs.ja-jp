---
title: "RemoveHandler ステートメント |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
dev_langs:
- VB
helpviewer_keywords:
- RemoveHandler keyword
- RemoveHandler statement
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
caps.latest.revision: 14
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
ms.openlocfilehash: d35de576bd9e267800acc2a9bfd5761dd977622f
ms.lasthandoff: 03/13/2017

---
# <a name="removehandler-statement"></a>RemoveHandler ステートメント
イベントとイベント ハンドラーの間の関連付けを削除します。  
  
## <a name="syntax"></a>構文  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`event`|処理されるイベントの名前。|  
|`eventhandler`|現在、イベントを処理するプロシージャの名前。|  
  
## <a name="remarks"></a>コメント  
 `AddHandler`と`RemoveHandler`ステートメントを使用すると、起動して、プログラムの実行中にいつでも、特定のイベントのイベント処理を停止します。  
  
> [!NOTE]
>  カスタム イベントの場合、`RemoveHandler`ステートメントで呼び出されるイベントの`RemoveHandler`アクセサー。 カスタム イベントの詳細については、次を参照してください。 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)します。  
  
## <a name="example"></a>例  
 [!code-vb[VbVbalrEvents&17;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [AddHandler ステートメント](../../../visual-basic/language-reference/statements/addhandler-statement.md)   
 [ハンドル](../../../visual-basic/language-reference/statements/handles-clause.md)   
 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)   
 [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)
