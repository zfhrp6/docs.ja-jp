---
title: "方法 : Visual Basic で接続ステータスをチェックする"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Web connections [Visual Basic]
- IsAvailable property [Visual Basic], about IsAvailable
- connections [Visual Basic], checking status
- connection status [Visual Basic]
ms.assetid: 4d9ee8ab-9a6f-4279-ace4-b75afc976a74
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 62361b4efff4c53156becf0cd865d262fbef1504
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-check-connection-status-in-visual-basic"></a><span data-ttu-id="be386-102">方法 : Visual Basic で接続ステータスをチェックする</span><span class="sxs-lookup"><span data-stu-id="be386-102">How to: Check Connection Status in Visual Basic</span></span>
<span data-ttu-id="be386-103">正常に動作しているネットワーク接続またはインターネット接続がコンピューターにあるかどうかは、<xref:Microsoft.VisualBasic.Devices.Network.IsAvailable%2A> プロパティを使って調べることができます。</span><span class="sxs-lookup"><span data-stu-id="be386-103">The <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable%2A> property can be used to determine whether the computer has a working network or Internet connection.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-check-whether-a-computer-has-a-working-connection"></a><span data-ttu-id="be386-104">正常に動作している接続がコンピューターにあるかどうかを調べるには</span><span class="sxs-lookup"><span data-stu-id="be386-104">To check whether a computer has a working connection</span></span>  
  
-   <span data-ttu-id="be386-105">`IsAvailable` プロパティが `True` であるか `False` であるかを調べます。</span><span class="sxs-lookup"><span data-stu-id="be386-105">Determine whether the `IsAvailable` property is `True` or `False`.</span></span> <span data-ttu-id="be386-106">このプロパティのステータスを調べて報告するコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="be386-106">The following code checks the property's status and reports it:</span></span>  
  
     [!code-vb[VbResourceTasks#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-check-connection-status_1.vb)]  
  
     <span data-ttu-id="be386-107">このコード例は、IntelliSense コード スニペットとしても利用できます。</span><span class="sxs-lookup"><span data-stu-id="be386-107">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="be386-108">コード スニペット ピッカーでは、これは **[接続とネットワーク]** にあります。</span><span class="sxs-lookup"><span data-stu-id="be386-108">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="be386-109">詳細については、「[Code Snippets](/visualstudio/ide/code-snippets)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be386-109">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be386-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="be386-110">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable%2A>
