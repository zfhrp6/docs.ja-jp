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
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="27856-102">Visual Basic での継承されたイベント ハンドラーのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="27856-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="27856-103">このトピックでは、継承されたコンポーネントのイベント ハンドラーで発生する一般的な問題を示します。</span><span class="sxs-lookup"><span data-stu-id="27856-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="27856-104">手順</span><span class="sxs-lookup"><span data-stu-id="27856-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="27856-105">呼び出しごとに 2 回実行されるコードのイベント ハンドラー</span><span class="sxs-lookup"><span data-stu-id="27856-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
-   <span data-ttu-id="27856-106">継承されたイベント ハンドラーを含めないでください、[処理](../../../../visual-basic/language-reference/statements/handles-clause.md)句。</span><span class="sxs-lookup"><span data-stu-id="27856-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="27856-107">基本クラスのメソッドは既にイベントに関連付けが発生します。</span><span class="sxs-lookup"><span data-stu-id="27856-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="27856-108">削除、`Handles`継承されたメソッドから句。</span><span class="sxs-lookup"><span data-stu-id="27856-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]  
  
-   <span data-ttu-id="27856-109">継承されたメソッドがない場合、`Handles`キーワード、コードに余分なが含まれていないことを確認してください。 [AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md)または同じイベントを処理する追加のメソッドです。</span><span class="sxs-lookup"><span data-stu-id="27856-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27856-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="27856-110">See Also</span></span>  
 [<span data-ttu-id="27856-111">イベント</span><span class="sxs-lookup"><span data-stu-id="27856-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
