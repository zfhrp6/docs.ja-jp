---
title: "Visual Basic での継承されたイベント ハンドラーのトラブルシューティング"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e0e8f0b669566bbee6530931bfba9808fad0c085
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="fac35-102">Visual Basic での継承されたイベント ハンドラーのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="fac35-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="fac35-103">このトピックでは、継承されたコンポーネントのイベント ハンドラーで発生する一般的な問題を示します。</span><span class="sxs-lookup"><span data-stu-id="fac35-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="fac35-104">手順</span><span class="sxs-lookup"><span data-stu-id="fac35-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="fac35-105">呼び出しごとに 2 回実行されるコードのイベント ハンドラー</span><span class="sxs-lookup"><span data-stu-id="fac35-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
-   <span data-ttu-id="fac35-106">継承されたイベント ハンドラーを含めないでください、[処理](../../../../visual-basic/language-reference/statements/handles-clause.md)句。</span><span class="sxs-lookup"><span data-stu-id="fac35-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="fac35-107">基本クラスのメソッドは既にイベントに関連付けが発生します。</span><span class="sxs-lookup"><span data-stu-id="fac35-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="fac35-108">削除、`Handles`継承されたメソッドから句。</span><span class="sxs-lookup"><span data-stu-id="fac35-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]  
  
-   <span data-ttu-id="fac35-109">継承されたメソッドがない場合、`Handles`キーワード、コードに余分なが含まれていないことを確認してください。 [AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md)または同じイベントを処理する追加のメソッドです。</span><span class="sxs-lookup"><span data-stu-id="fac35-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fac35-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="fac35-110">See Also</span></span>  
 [<span data-ttu-id="fac35-111">イベント</span><span class="sxs-lookup"><span data-stu-id="fac35-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
