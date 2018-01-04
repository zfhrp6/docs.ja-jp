---
title: "方法 : カスタム コンテキスト メニューを RichTextBox に配置する"
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
- custom context menus [WPF], positioning
- positioning custom context menus [WPF]
- RichTextBox control [WPF], positioning custom context menus
- context menus [WPF], positioning
ms.assetid: bf77c930-a546-4573-9a56-9af345ba189a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4651953ec8ae6373b9a6946b31f96213bec570cc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-position-a-custom-context-menu-in-a-richtextbox"></a><span data-ttu-id="325aa-102">方法 : カスタム コンテキスト メニューを RichTextBox に配置する</span><span class="sxs-lookup"><span data-stu-id="325aa-102">How to: Position a Custom Context Menu in a RichTextBox</span></span>
<span data-ttu-id="325aa-103">この例では、配置用のカスタムのコンテキスト メニュー、<xref:System.Windows.Controls.RichTextBox>です。</span><span class="sxs-lookup"><span data-stu-id="325aa-103">This example shows how to position a custom context menu for a <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
 <span data-ttu-id="325aa-104">**RichTextBox** のカスタム コンテキスト メニューを実装する場合、コンテキスト メニューの配置の処理を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="325aa-104">When you implement a custom context menu for a **RichTextBox**, you are responsible for handling the placement of the context menu.</span></span>  <span data-ttu-id="325aa-105">既定では、**RichTextBox** の中央でカスタム コンテキスト メニューが開きます。</span><span class="sxs-lookup"><span data-stu-id="325aa-105">By default, a custom context menu is opened at the center of the **RichTextBox**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="325aa-106">例</span><span class="sxs-lookup"><span data-stu-id="325aa-106">Example</span></span>  
 <span data-ttu-id="325aa-107">既定の配置の動作を無効にする追加のリスナーを<xref:System.Windows.FrameworkContentElement.ContextMenuOpening>イベント。</span><span class="sxs-lookup"><span data-stu-id="325aa-107">To override the default placement behavior, add a listener for the <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> event.</span></span>  <span data-ttu-id="325aa-108">次の例では、プログラムによってこれを実行する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="325aa-108">The following example shows how to do this programmatically.</span></span>  
  
 [!code-csharp[RichTextBox_ContextMenu#_AddListener](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_addlistener)]
 [!code-vb[RichTextBox_ContextMenu#_AddListener](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_addlistener)]  
  
## <a name="example"></a><span data-ttu-id="325aa-109">例</span><span class="sxs-lookup"><span data-stu-id="325aa-109">Example</span></span>  
 <span data-ttu-id="325aa-110">次の例は、対応する実装を示します<xref:System.Windows.FrameworkContentElement.ContextMenuOpening>イベント リスナー。</span><span class="sxs-lookup"><span data-stu-id="325aa-110">The following example shows an implementation the corresponding <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> event listener.</span></span>  
  
 [!code-csharp[RichTextBox_ContextMenu#_ListenerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_listenerbody)]
 [!code-vb[RichTextBox_ContextMenu#_ListenerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_listenerbody)]  
  
## <a name="see-also"></a><span data-ttu-id="325aa-111">参照</span><span class="sxs-lookup"><span data-stu-id="325aa-111">See Also</span></span>  
 [<span data-ttu-id="325aa-112">RichTextBox の概要</span><span class="sxs-lookup"><span data-stu-id="325aa-112">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [<span data-ttu-id="325aa-113">TextBox の概要</span><span class="sxs-lookup"><span data-stu-id="325aa-113">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
