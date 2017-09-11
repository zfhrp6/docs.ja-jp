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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: f64395975821226d42664bbf78b04120d49a38bc
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="d1214-102">Visual Basic での継承されたイベント ハンドラーのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="d1214-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="d1214-103">このトピックでは、継承されたコンポーネントでイベント ハンドラーで発生する一般的な問題を示します。</span><span class="sxs-lookup"><span data-stu-id="d1214-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="d1214-104">手順</span><span class="sxs-lookup"><span data-stu-id="d1214-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="d1214-105">イベント ハンドラーのコードを呼び出しごとに&2; 回実行します。</span><span class="sxs-lookup"><span data-stu-id="d1214-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
-   <span data-ttu-id="d1214-106">継承されたイベント ハンドラーを含めないでください、[処理](../../../../visual-basic/language-reference/statements/handles-clause.md)句。</span><span class="sxs-lookup"><span data-stu-id="d1214-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="d1214-107">基本クラスのメソッドには既にイベントに関連付けが発生します。</span><span class="sxs-lookup"><span data-stu-id="d1214-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="d1214-108">削除、`Handles`継承されたメソッドから句。</span><span class="sxs-lookup"><span data-stu-id="d1214-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     <span data-ttu-id="d1214-109">[!code-vb[VbVbalrEvents&#32;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d1214-109">[!code-vb[VbVbalrEvents#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]</span></span>  
  
-   <span data-ttu-id="d1214-110">継承されたメソッドがあるない場合、`Handles`キーワード、余分なにコードが含まれていないことを確認[AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md)または他のメソッドを同じイベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="d1214-110">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1214-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="d1214-111">See Also</span></span>  
 [<span data-ttu-id="d1214-112">イベント</span><span class="sxs-lookup"><span data-stu-id="d1214-112">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
