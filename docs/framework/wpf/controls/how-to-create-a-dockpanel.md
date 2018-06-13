---
title: '方法 : DockPanel を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], creating
ms.assetid: 9194f663-e279-4f1a-86d7-125a57d05c6f
ms.openlocfilehash: 4382314b0fe5385c158af9764ccb0067b741a693
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33550151"
---
# <a name="how-to-create-a-dockpanel"></a><span data-ttu-id="cf5ce-102">方法 : DockPanel を作成する</span><span class="sxs-lookup"><span data-stu-id="cf5ce-102">How to: Create a DockPanel</span></span>
## <a name="example"></a><span data-ttu-id="cf5ce-103">例</span><span class="sxs-lookup"><span data-stu-id="cf5ce-103">Example</span></span>  
 <span data-ttu-id="cf5ce-104">次の例は、作成しのインスタンスを使用して<xref:System.Windows.Controls.DockPanel>コードを使用しています。</span><span class="sxs-lookup"><span data-stu-id="cf5ce-104">The following example creates and uses an instance of <xref:System.Windows.Controls.DockPanel> by using code.</span></span> <span data-ttu-id="cf5ce-105">例は、5 つ作成することで領域をパーティション分割する方法を示します<xref:System.Windows.Shapes.Rectangle>要素および配置 (ドッキング) 親内に<xref:System.Windows.Controls.DockPanel>です。</span><span class="sxs-lookup"><span data-stu-id="cf5ce-105">The example shows you how to partition space by creating five <xref:System.Windows.Shapes.Rectangle> elements and positioning (docking) them inside a parent <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="cf5ce-106">既定の設定を保持する場合、最後の四角形は、残りのすべての未割り当て領域を塗りつぶします。</span><span class="sxs-lookup"><span data-stu-id="cf5ce-106">If you retain the default setting, the final rectangle fills all the remaining unallocated space.</span></span>  
  
 [!code-csharp[DockPanelCode#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelCode/CSharp/DockPanel_Code.cs#1)]
 [!code-vb[DockPanelCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelCode/VisualBasic/dockpanel_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="cf5ce-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="cf5ce-107">See Also</span></span>  
 <xref:System.Windows.Controls.DockPanel>  
 <xref:System.Windows.Controls.Dock>  
 [<span data-ttu-id="cf5ce-108">パネルの概要</span><span class="sxs-lookup"><span data-stu-id="cf5ce-108">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
