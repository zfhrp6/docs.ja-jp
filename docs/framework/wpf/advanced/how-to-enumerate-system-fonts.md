---
title: "方法 : システム フォントを列挙する"
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
- typography [WPF], enumerating system fonts
- fonts [WPF], enumerating
- system fonts [WPF], enumerating
- enumerating [WPF], system fonts
ms.assetid: 36e37791-55b9-4f01-a496-5cc10335e6a6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cf917dc2af256cdd0f3a0c579f86847e1bf4f1e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enumerate-system-fonts"></a><span data-ttu-id="cffef-102">方法 : システム フォントを列挙する</span><span class="sxs-lookup"><span data-stu-id="cffef-102">How to: Enumerate System Fonts</span></span>
## <a name="example"></a><span data-ttu-id="cffef-103">例</span><span class="sxs-lookup"><span data-stu-id="cffef-103">Example</span></span>  
 <span data-ttu-id="cffef-104">次の例では、システム フォントのコレクション内のフォントを列挙する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="cffef-104">The following example shows how to enumerate the fonts in the system font collection.</span></span> <span data-ttu-id="cffef-105">それぞれのフォント ファミリ名<xref:System.Windows.Media.FontFamily>内<xref:System.Windows.Media.Fonts.SystemFontFamilies%2A>コンボ ボックスにアイテムとして追加します。</span><span class="sxs-lookup"><span data-stu-id="cffef-105">The font family name of each <xref:System.Windows.Media.FontFamily> within <xref:System.Windows.Media.Fonts.SystemFontFamilies%2A> is added as an item to a combo box.</span></span>  
  
 [!code-csharp[TextOverview#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextOverview#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextOverview/visualbasic/window1.xaml.vb#100)]  
  
 <span data-ttu-id="cffef-106">同じフォント ファミリの複数のバージョンが、同じディレクトリに存在する場合、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]フォント列挙には、フォントの最新バージョンが返されます。</span><span class="sxs-lookup"><span data-stu-id="cffef-106">If multiple versions of the same font family reside in the same directory, the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] font enumeration returns the most recent version of the font.</span></span> <span data-ttu-id="cffef-107">バージョン情報は、解決を提供していない、最新のタイムスタンプを持つフォントが返されます。</span><span class="sxs-lookup"><span data-stu-id="cffef-107">If the version information does not provide resolution, the font with latest timestamp is returned.</span></span> <span data-ttu-id="cffef-108">タイムスタンプ情報が同等の場合は、アルファベット順の最初のフォント ファイルが返されます。</span><span class="sxs-lookup"><span data-stu-id="cffef-108">If the timestamp information is equivalent, the font file that is first in alphabetical order is returned.</span></span>
