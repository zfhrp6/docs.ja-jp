---
title: "方法 : StackPanel を作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- StackPanel control [WPF], creating
ms.assetid: e7ce65cb-720a-4bb6-95b6-286b74488a58
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9226ac10e4f221cc381b7c59179b2667e20aa757
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-stackpanel"></a><span data-ttu-id="a276b-102">方法 : StackPanel を作成する</span><span class="sxs-lookup"><span data-stu-id="a276b-102">How to: Create a StackPanel</span></span>
<span data-ttu-id="a276b-103">この例を作成する方法を示しています、<xref:System.Windows.Controls.StackPanel>です。</span><span class="sxs-lookup"><span data-stu-id="a276b-103">This example shows how to create a <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a276b-104">例</span><span class="sxs-lookup"><span data-stu-id="a276b-104">Example</span></span>  
 <span data-ttu-id="a276b-105">A<xref:System.Windows.Controls.StackPanel>指定した方向に要素をスタックすることができます。</span><span class="sxs-lookup"><span data-stu-id="a276b-105">A <xref:System.Windows.Controls.StackPanel> allows you to stack elements in a specified direction.</span></span> <span data-ttu-id="a276b-106">定義されているプロパティを使用して<xref:System.Windows.Controls.StackPanel>、コンテンツ フローできます両方垂直方向には、これは既定の設定、または水平方向にします。</span><span class="sxs-lookup"><span data-stu-id="a276b-106">By using properties that are defined on <xref:System.Windows.Controls.StackPanel>, content can flow both vertically, which is the default setting, or horizontally.</span></span>  
  
 <span data-ttu-id="a276b-107">5 は、次の例が垂直方向に積み上げ<xref:System.Windows.Controls.TextBlock>制御する場合に、それぞれ異なる<xref:System.Windows.Controls.Border>と<xref:System.Windows.Controls.Border.Background%2A>を使用して<xref:System.Windows.Controls.StackPanel>です。</span><span class="sxs-lookup"><span data-stu-id="a276b-107">The following example vertically stacks five <xref:System.Windows.Controls.TextBlock> controls, each with a different <xref:System.Windows.Controls.Border> and <xref:System.Windows.Controls.Border.Background%2A>, by using <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="a276b-108">指定されて子要素<xref:System.Windows.FrameworkElement.Width%2A>stretch を親ウィンドウです。 ただし、子要素がある、指定した<xref:System.Windows.FrameworkElement.Width%2A>、ウィンドウ内で中央揃えで配置しません。</span><span class="sxs-lookup"><span data-stu-id="a276b-108">The child elements that have no specified <xref:System.Windows.FrameworkElement.Width%2A> stretch to fill the parent window; however, the child elements that have a specified <xref:System.Windows.FrameworkElement.Width%2A>, are centered within the window.</span></span>  
  
 <span data-ttu-id="a276b-109">既定のスタック方向、<xref:System.Windows.Controls.StackPanel>は縦方向です。</span><span class="sxs-lookup"><span data-stu-id="a276b-109">The default stack direction in a <xref:System.Windows.Controls.StackPanel> is vertical.</span></span> <span data-ttu-id="a276b-110">コントロールのコンテンツ フローに、<xref:System.Windows.Controls.StackPanel>を使用して、<xref:System.Windows.Controls.StackPanel.Orientation%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="a276b-110">To control content flow in a <xref:System.Windows.Controls.StackPanel>, use the <xref:System.Windows.Controls.StackPanel.Orientation%2A> property.</span></span> <span data-ttu-id="a276b-111">使用して、水平方向の配置を制御することができます、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="a276b-111">You can control horizontal alignment by using the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property.</span></span>  
  
```xaml  
<Page xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" WindowTitle="StackPanel Sample">  
  <StackPanel>  
    <Border Background="SkyBlue" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="12">Stacked Item #1</TextBlock>  
    </Border>  
    <Border Width="400" Background="CadetBlue" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="14">Stacked Item #2</TextBlock>  
    </Border>  
    <Border Background="LightGoldenRodYellow" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="16">Stacked Item #3</TextBlock>  
    </Border>  
    <Border Width="200" Background="PaleGreen" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="18">Stacked Item #4</TextBlock>  
    </Border>  
    <Border Background="White" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="20">Stacked Item #5</TextBlock>  
    </Border>  
  </StackPanel>  
</Page>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a276b-112">参照</span><span class="sxs-lookup"><span data-stu-id="a276b-112">See Also</span></span>  
 <xref:System.Windows.Controls.StackPanel>  
 [<span data-ttu-id="a276b-113">パネルの概要</span><span class="sxs-lookup"><span data-stu-id="a276b-113">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="a276b-114">方法トピック</span><span class="sxs-lookup"><span data-stu-id="a276b-114">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/stackpanel-how-to-topics.md)
