---
title: '方法 : ToolBar のコントロールのスタイルを指定する'
ms.date: 03/30/2017
helpviewer_keywords:
- styling controls on toolbar [WPF]
- toolbars [WPF]
- customizing controls on toolbar [WPF]
ms.assetid: ba6ae056-d6a9-4c24-90f8-467ab0bc0b1a
ms.openlocfilehash: cc5ac9dd64072c34ff999255a27dd92f311cda0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551818"
---
# <a name="how-to-style-controls-on-a-toolbar"></a><span data-ttu-id="1db5a-102">方法 : ToolBar のコントロールのスタイルを指定する</span><span class="sxs-lookup"><span data-stu-id="1db5a-102">How to: Style Controls on a ToolBar</span></span>
<span data-ttu-id="1db5a-103"><xref:System.Windows.Controls.ToolBar>定義<xref:System.Windows.ResourceKey>内のコントロールのスタイルを指定するオブジェクト、<xref:System.Windows.Controls.ToolBar>です。</span><span class="sxs-lookup"><span data-stu-id="1db5a-103">The <xref:System.Windows.Controls.ToolBar> defines <xref:System.Windows.ResourceKey> objects to specify the style of controls within the <xref:System.Windows.Controls.ToolBar>.</span></span>  <span data-ttu-id="1db5a-104">内のコントロールのスタイルを設定する、 <xref:System.Windows.Controls.ToolBar>、設定、`x:key`するスタイルの属性、<xref:System.Windows.ResourceKey>で定義されている<xref:System.Windows.Controls.ToolBar>です。</span><span class="sxs-lookup"><span data-stu-id="1db5a-104">To style a control in a <xref:System.Windows.Controls.ToolBar>, set the `x:key` attribute of the style to a <xref:System.Windows.ResourceKey> defined in <xref:System.Windows.Controls.ToolBar>.</span></span>  
  
 <span data-ttu-id="1db5a-105"><xref:System.Windows.Controls.ToolBar> 、次を定義<xref:System.Windows.ResourceKey>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="1db5a-105">The <xref:System.Windows.Controls.ToolBar> defines the following <xref:System.Windows.ResourceKey> objects:</span></span>  
  
-   <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.CheckBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.MenuStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.RadioButtonStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.SeparatorStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.TextBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.ToggleButtonStyleKey%2A>  
  
## <a name="example"></a><span data-ttu-id="1db5a-106">例</span><span class="sxs-lookup"><span data-stu-id="1db5a-106">Example</span></span>  
 <span data-ttu-id="1db5a-107">次の例の定義内でコントロールのスタイル、<xref:System.Windows.Controls.ToolBar>です。</span><span class="sxs-lookup"><span data-stu-id="1db5a-107">The following example defines styles for the controls within a <xref:System.Windows.Controls.ToolBar>.</span></span>  
  
 [!code-xaml[ToolBar_snip#ToolBarAllStyles](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbarallstyles)]  
[!code-xaml[ToolBar_snip#ToolBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbar)]  
  
## <a name="see-also"></a><span data-ttu-id="1db5a-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="1db5a-108">See Also</span></span>  
 [<span data-ttu-id="1db5a-109">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="1db5a-109">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
