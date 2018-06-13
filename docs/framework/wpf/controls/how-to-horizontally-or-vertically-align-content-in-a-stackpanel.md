---
title: '方法 : StackPanel にコンテンツを水平方向または垂直方向に配置する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StackPanel control [WPF], content alignment [WPF]
- content alignment [WPF]
- aligning [WPF], content
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
ms.openlocfilehash: a03cb1ed9b3e5bd42b28e37f5bbb3e1d0446a4ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33550755"
---
# <a name="how-to-horizontally-or-vertically-align-content-in-a-stackpanel"></a><span data-ttu-id="50c44-102">方法 : StackPanel にコンテンツを水平方向または垂直方向に配置する</span><span class="sxs-lookup"><span data-stu-id="50c44-102">How to: Horizontally or Vertically Align Content in a StackPanel</span></span>
<span data-ttu-id="50c44-103">この例では、調整、<xref:System.Windows.Controls.StackPanel.Orientation%2A>内のコンテンツの<xref:System.Windows.Controls.StackPanel>を調整する方法と、要素、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>と<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>子コンテンツのです。</span><span class="sxs-lookup"><span data-stu-id="50c44-103">This example shows how to adjust the <xref:System.Windows.Controls.StackPanel.Orientation%2A> of content within a <xref:System.Windows.Controls.StackPanel> element, and also how to adjust the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> of child content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50c44-104">例</span><span class="sxs-lookup"><span data-stu-id="50c44-104">Example</span></span>  
 <span data-ttu-id="50c44-105">次の例では、3 つが作成されます<xref:System.Windows.Controls.ListBox>内の要素[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="50c44-105">The following example creates three <xref:System.Windows.Controls.ListBox> elements in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="50c44-106">各<xref:System.Windows.Controls.ListBox>の有効な値を表す、 <xref:System.Windows.Controls.StackPanel.Orientation%2A>、 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、および<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>のプロパティ、<xref:System.Windows.Controls.StackPanel>です。</span><span class="sxs-lookup"><span data-stu-id="50c44-106">Each <xref:System.Windows.Controls.ListBox> represents the possible values of the <xref:System.Windows.Controls.StackPanel.Orientation%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> properties of a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="50c44-107">ユーザーがのいずれかの値を選択すると、<xref:System.Windows.Controls.ListBox>要素、関連付けられたプロパティの<xref:System.Windows.Controls.StackPanel>とその子<xref:System.Windows.Controls.Button>要素を変更します。</span><span class="sxs-lookup"><span data-stu-id="50c44-107">When a user selects a value in any of the <xref:System.Windows.Controls.ListBox> elements, the associated property of the <xref:System.Windows.Controls.StackPanel> and its child <xref:System.Windows.Controls.Button> elements change.</span></span>  
  
 [!code-xaml[StackPanelIntroSamp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="50c44-108">次の分離コード ファイルに関連付けられているイベントに変更を定義する、<xref:System.Windows.Controls.ListBox>選択範囲が変更されます。</span><span class="sxs-lookup"><span data-stu-id="50c44-108">The following code-behind file defines the changes to the events that are associated with the <xref:System.Windows.Controls.ListBox> selection changes.</span></span> <span data-ttu-id="50c44-109"><xref:System.Windows.Controls.StackPanel> によって識別される、 <xref:System.Windows.FrameworkElement.Name%2A> `sp1`です。</span><span class="sxs-lookup"><span data-stu-id="50c44-109"><xref:System.Windows.Controls.StackPanel> is identified by the <xref:System.Windows.FrameworkElement.Name%2A> `sp1`.</span></span>  
  
 [!code-csharp[StackPanelIntroSamp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="50c44-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="50c44-110">See Also</span></span>  
 <xref:System.Windows.Controls.StackPanel>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>  
 [<span data-ttu-id="50c44-111">パネルの概要</span><span class="sxs-lookup"><span data-stu-id="50c44-111">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
