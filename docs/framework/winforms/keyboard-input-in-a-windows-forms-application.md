---
title: "Windows フォーム アプリケーションにおけるキーボード入力"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- keyboard input [Windows Forms], using in Windows Forms
- keyboards [Windows Forms], keyboard input
- Windows Forms, keyboard input
ms.assetid: 68f5bc70-14d5-45c9-b288-7d7b1493ee79
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 256fb961c01b17c21613fe4ec60b8e7f68c2d8f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="keyboard-input-in-a-windows-forms-application"></a><span data-ttu-id="297c4-102">Windows フォーム アプリケーションにおけるキーボード入力</span><span class="sxs-lookup"><span data-stu-id="297c4-102">Keyboard Input in a Windows Forms Application</span></span>
<span data-ttu-id="297c4-103">Windows フォームでは、標準のキーボードおよびイベントを特定のキー入力に応答することは、傍受、変更、およびアプリケーションでは、フォーム、キーの押下を消費およびレベルを制御するための方法も含まれます。</span><span class="sxs-lookup"><span data-stu-id="297c4-103">Windows Forms includes standard keyboard events that allow you to respond to specific key presses, and also provides ways for you to intercept, modify, and consume key presses at the application, form, and control level.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="297c4-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="297c4-104">In This Section</span></span>  
 [<span data-ttu-id="297c4-105">キーボード入力のしくみ</span><span class="sxs-lookup"><span data-stu-id="297c4-105">How Keyboard Input Works</span></span>](../../../docs/framework/winforms/how-keyboard-input-works.md)  
 <span data-ttu-id="297c4-106">キーボード メッセージを処理し、キーボード イベントに変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="297c4-106">Describes how keyboard messages are processed and transformed into keyboard events.</span></span>  
  
 [<span data-ttu-id="297c4-107">キーボード イベントの使用</span><span class="sxs-lookup"><span data-stu-id="297c4-107">Using Keyboard Events</span></span>](../../../docs/framework/winforms/using-keyboard-events.md)  
 <span data-ttu-id="297c4-108">キーボード イベントとキーボード イベント ハンドラーによって受信される情報の種類について説明します。</span><span class="sxs-lookup"><span data-stu-id="297c4-108">Provides information on the types of keyboard events and the information that is received by the keyboard event handlers.</span></span>  
  
 [<span data-ttu-id="297c4-109">方法: キーボード入力を標準コントロールに変更する</span><span class="sxs-lookup"><span data-stu-id="297c4-109">How to: Modify Keyboard Input to a Standard Control</span></span>](../../../docs/framework/winforms/how-to-modify-keyboard-input-to-a-standard-control.md)  
 <span data-ttu-id="297c4-110">コントロールに到達する前に、キーの値を変更する方法を示すコード例を表示します。</span><span class="sxs-lookup"><span data-stu-id="297c4-110">Presents a code example that shows how to modify key values before they reach a control.</span></span>  
  
 [<span data-ttu-id="297c4-111">方法: どの修飾子キーが押されたかを判断する</span><span class="sxs-lookup"><span data-stu-id="297c4-111">How to: Determine Which Modifier Key Was Pressed</span></span>](../../../docs/framework/winforms/how-to-determine-which-modifier-key-was-pressed.md)  
 <span data-ttu-id="297c4-112">SHIFT、alt キーを押し、または ctrl キーを別のキーだけでなく押されたかどうかを確認する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="297c4-112">Demonstrates how to find out whether SHIFT, ALT, or CTRL was pressed in addition to another key.</span></span>  
  
 [<span data-ttu-id="297c4-113">方法: キーボード入力をフォーム レベルで処理する</span><span class="sxs-lookup"><span data-stu-id="297c4-113">How to: Handle Keyboard Input at the Form Level</span></span>](../../../docs/framework/winforms/how-to-handle-keyboard-input-at-the-form-level.md)  
 <span data-ttu-id="297c4-114">コントロールに到達する前に、キーをインターセプトする方法を示すコード例を表示します。</span><span class="sxs-lookup"><span data-stu-id="297c4-114">Presents a code example that shows how to intercept keys before they reach a control.</span></span>
