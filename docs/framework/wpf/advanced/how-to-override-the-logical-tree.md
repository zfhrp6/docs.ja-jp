---
title: '方法: 論理ツリーをオーバーライドする'
ms.date: 03/30/2017
helpviewer_keywords:
- overriding the logical tree [WPF]
- logical tree [WPF], overriding
ms.assetid: 0ae4d074-8113-4b06-b4fa-e0f39d4967a6
ms.openlocfilehash: 0c7269b9ea052019e2e4f6def23b063903cbb5e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-override-the-logical-tree"></a><span data-ttu-id="d1237-102">方法: 論理ツリーをオーバーライドする</span><span class="sxs-lookup"><span data-stu-id="d1237-102">How to: Override the Logical Tree</span></span>
<span data-ttu-id="d1237-103">ほとんどの場合は必要ありませんが、高度なコントロールを作成する場合は、必要に応じて論理ツリーをオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="d1237-103">Although it is not necessary in most cases, advanced control authors have the option to override the logical tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1237-104">例</span><span class="sxs-lookup"><span data-stu-id="d1237-104">Example</span></span>  
 <span data-ttu-id="d1237-105">この例ではサブクラス<xref:System.Windows.Controls.StackPanel>パネルがだけし、単一の子要素は表示のみの動作を適用ここでは、論理ツリーをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="d1237-105">This example describes how to subclass <xref:System.Windows.Controls.StackPanel> to override the logical tree, in this case to enforce a behavior that the panel may only have and will only render a single child element.</span></span> <span data-ttu-id="d1237-106">これは実際的には必ずしも好ましい動作ではありませんが、ここでは要素の通常の論理ツリーをオーバーライドするシナリオを説明するための手段として示します。</span><span class="sxs-lookup"><span data-stu-id="d1237-106">This isn't necessarily a practically desirable behavior, but is shown here as a means of illustrating the scenario for overriding an element's normal logical tree.</span></span>  
  
 [!code-csharp[LogicalOverride#SingletonPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 <span data-ttu-id="d1237-107">論理ツリーについて詳しくは、「[WPF のツリー](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d1237-107">For more information on the logical tree, see [Trees in WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).</span></span>
