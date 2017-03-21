---
title: "継承された Visual Basic でのイベント ハンドラーのトラブルシューティング |Microsoft ドキュメント"
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
- troubleshooting events
- inherited events
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
caps.latest.revision: 11
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
ms.openlocfilehash: 0dae6b48b1885a52b99ae3e7328340cac7b2d7d4
ms.lasthandoff: 03/13/2017

---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a>Visual Basic での継承されたイベント ハンドラーのトラブルシューティング
このトピックでは、継承されたコンポーネントでイベント ハンドラーで発生する一般的な問題を示します。  
  
## <a name="procedures"></a>手順  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a>イベント ハンドラーのコードを呼び出しごとに&2; 回実行します。  
  
-   継承されたイベント ハンドラーを含めないでください、[処理](../../../../visual-basic/language-reference/statements/handles-clause.md)句。 基本クラスのメソッドには既にイベントに関連付けが発生します。 削除、`Handles`継承されたメソッドから句。  
  
     [!code-vb[VbVbalrEvents&#32;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]  
  
-   継承されたメソッドがあるない場合、`Handles`キーワード、余分なにコードが含まれていないことを確認[AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md)または他のメソッドを同じイベントを処理します。  
  
## <a name="see-also"></a>関連項目  
 [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)
