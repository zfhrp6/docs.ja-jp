---
title: Visual Basic での継承されたイベント ハンドラーのトラブルシューティング
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
ms.openlocfilehash: f6355cf7fc2e43651c1112d048220a8179968c76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646330"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a>Visual Basic での継承されたイベント ハンドラーのトラブルシューティング
このトピックでは、継承されたコンポーネントのイベント ハンドラーで発生する一般的な問題を示します。  
  
## <a name="procedures"></a>手順  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a>呼び出しごとに 2 回実行されるコードのイベント ハンドラー  
  
-   継承されたイベント ハンドラーを含めないでください、[処理](../../../../visual-basic/language-reference/statements/handles-clause.md)句。 基本クラスのメソッドは既にイベントに関連付けが発生します。 削除、`Handles`継承されたメソッドから句。  
  
     [!code-vb[VbVbalrEvents#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]  
  
-   継承されたメソッドがない場合、`Handles`キーワード、コードに余分なが含まれていないことを確認してください。 [AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md)または同じイベントを処理する追加のメソッドです。  
  
## <a name="see-also"></a>関連項目  
 [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)
