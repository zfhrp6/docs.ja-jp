---
title: '方法 : ThicknessConverter オブジェクトを使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- border thickness [WPF]
- ThicknessConverter objects [WPF]
ms.assetid: 52682194-d7fd-499c-8005-73fcc84e7b2c
ms.openlocfilehash: 119c4397dee76429e776378ee89fa49747dbfce4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544344"
---
# <a name="how-to-use-a-thicknessconverter-object"></a><span data-ttu-id="dcd4f-102">方法 : ThicknessConverter オブジェクトを使用する</span><span class="sxs-lookup"><span data-stu-id="dcd4f-102">How to: Use a ThicknessConverter Object</span></span>
## <a name="example"></a><span data-ttu-id="dcd4f-103">例</span><span class="sxs-lookup"><span data-stu-id="dcd4f-103">Example</span></span>  
 <span data-ttu-id="dcd4f-104">この例は、のインスタンスを作成する方法を示しています。<xref:System.Windows.ThicknessConverter>境界線の太さを変更するとします。</span><span class="sxs-lookup"><span data-stu-id="dcd4f-104">This example shows how to create an instance of <xref:System.Windows.ThicknessConverter> and use it to change the thickness of a border.</span></span>  
  
 <span data-ttu-id="dcd4f-105">例と呼ばれるカスタム メソッドを定義する`changeThickness`; このメソッドは最初のコンテンツを変換、<xref:System.Windows.Controls.ListBoxItem>個別で定義されている、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ファイルのインスタンスを<xref:System.Windows.Thickness>、後に、コンテンツに変換します、<xref:System.String>です。</span><span class="sxs-lookup"><span data-stu-id="dcd4f-105">The example defines a custom method called `changeThickness`; this method first converts the contents of a <xref:System.Windows.Controls.ListBoxItem>, as defined in a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file, to an instance of <xref:System.Windows.Thickness>, and later converts the content into a <xref:System.String>.</span></span> <span data-ttu-id="dcd4f-106">このメソッドは、<xref:System.Windows.Controls.ListBoxItem>を<xref:System.Windows.ThicknessConverter>に変換するオブジェクト、<xref:System.Windows.Controls.ContentControl.Content%2A>の<xref:System.Windows.Controls.ListBoxItem>のインスタンスに<xref:System.Windows.Thickness>です。</span><span class="sxs-lookup"><span data-stu-id="dcd4f-106">This method passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.ThicknessConverter> object, which converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Windows.Thickness>.</span></span> <span data-ttu-id="dcd4f-107">この値がの値として渡されたし、<xref:System.Windows.Controls.Border.BorderThickness%2A>のプロパティ、<xref:System.Windows.Controls.Border>です。</span><span class="sxs-lookup"><span data-stu-id="dcd4f-107">This value is then passed back as the value of the <xref:System.Windows.Controls.Border.BorderThickness%2A> property of the <xref:System.Windows.Controls.Border>.</span></span>  
  
 <span data-ttu-id="dcd4f-108">この例は実行できません。</span><span class="sxs-lookup"><span data-stu-id="dcd4f-108">This example does not run.</span></span>  
  
 [!code-csharp[ThicknessConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThicknessConverter/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ThicknessConverter#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThicknessConverter/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="dcd4f-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="dcd4f-109">See Also</span></span>  
 <xref:System.Windows.Thickness>  
 <xref:System.Windows.ThicknessConverter>  
 <xref:System.Windows.Controls.Border>  
 [<span data-ttu-id="dcd4f-110">方法: Margin プロパティの変更</span><span class="sxs-lookup"><span data-stu-id="dcd4f-110">How to: Change the Margin Property</span></span>](http://msdn.microsoft.com/library/8a313efd-5f99-4097-b4c1-8fa49d8379a2)  
 [<span data-ttu-id="dcd4f-111">方法: ListBoxItem を新しいデータ型に変換します。</span><span class="sxs-lookup"><span data-stu-id="dcd4f-111">How to: Convert a ListBoxItem to a new Data Type</span></span>](http://msdn.microsoft.com/library/7a080b88-184e-4b27-bb61-d42bafba9727)  
 [<span data-ttu-id="dcd4f-112">パネルの概要</span><span class="sxs-lookup"><span data-stu-id="dcd4f-112">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
