---
title: "方法 : アプリケーション ジェスチャを認識する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application gestures [WPF], recognizing
- gestures [WPF], recognizing
ms.assetid: d58b740f-5192-4a3e-af59-7aa162e6ca15
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 24d9e4435362f5f87185d04f911caf76517a0de9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-recognize-application-gestures"></a><span data-ttu-id="fc9dc-102">方法 : アプリケーション ジェスチャを認識する</span><span class="sxs-lookup"><span data-stu-id="fc9dc-102">How To: Recognize Application Gestures</span></span>
<span data-ttu-id="fc9dc-103">次の例は、ユーザーが、インクを消去する方法を示します、<xref:System.Windows.Ink.ApplicationGesture.ScratchOut>にジェスチャ、<xref:System.Windows.Controls.InkCanvas>です。</span><span class="sxs-lookup"><span data-stu-id="fc9dc-103">The following example demonstrates how to erase ink when a user makes a <xref:System.Windows.Ink.ApplicationGesture.ScratchOut> gesture on an <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="fc9dc-104">この例では、<xref:System.Windows.Controls.InkCanvas>という`inkCanvas1`、XAML ファイルで宣言されています。</span><span class="sxs-lookup"><span data-stu-id="fc9dc-104">This example assumes an <xref:System.Windows.Controls.InkCanvas>, called `inkCanvas1`, is declared in the XAML file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc9dc-105">例</span><span class="sxs-lookup"><span data-stu-id="fc9dc-105">Example</span></span>  
 [!code-csharp[HowToRecognizeGestures#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToRecognizeGestures/CSharp/Window1.xaml.cs#1)]
 [!code-vb[HowToRecognizeGestures#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToRecognizeGestures/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="fc9dc-106">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc9dc-106">See Also</span></span>  
 <xref:System.Windows.Ink.ApplicationGesture>  
 <xref:System.Windows.Controls.InkCanvas>  
 <xref:System.Windows.Controls.InkCanvas.Gesture>
