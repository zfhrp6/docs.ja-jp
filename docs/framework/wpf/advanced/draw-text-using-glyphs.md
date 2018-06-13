---
title: グリフを使用したテキストの描画
ms.date: 03/30/2017
helpviewer_keywords:
- text [WPF], drawing with Glyphs objects
- Glyphs objects [WPF], drawing text
- typography [WPF], Glyphs objects
ms.assetid: 587ab17e-a419-4ad5-b6da-8933a8e83d97
ms.openlocfilehash: e2b35eb6df140551d5db7d597826df53e37182fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542527"
---
# <a name="draw-text-using-glyphs"></a><span data-ttu-id="55eb1-102">グリフを使用したテキストの描画</span><span class="sxs-lookup"><span data-stu-id="55eb1-102">Draw Text Using Glyphs</span></span>
<span data-ttu-id="55eb1-103">このトピックの内容が、低レベルの使用方法について説明します<xref:System.Windows.Documents.Glyphs>内のテキストを表示するオブジェクト[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="55eb1-103">This topic explains how to use the low-level <xref:System.Windows.Documents.Glyphs> object to display text in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="55eb1-104">例</span><span class="sxs-lookup"><span data-stu-id="55eb1-104">Example</span></span>  
 <span data-ttu-id="55eb1-105">次の例のプロパティを定義する方法を示して、<xref:System.Windows.Documents.Glyphs>オブジェクトに[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="55eb1-105">The following examples show how to define properties for a <xref:System.Windows.Documents.Glyphs> object in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="55eb1-106"><xref:System.Windows.Documents.Glyphs>オブジェクトの出力を表す、<xref:System.Windows.Media.GlyphRun>で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="55eb1-106">The <xref:System.Windows.Documents.Glyphs> object represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="55eb1-107">この例では、Arial、Courier New、Times New Roman フォントがローカル コンピューターの C:\WINDOWS\Fonts フォルダーにインストールされていると想定しています。</span><span class="sxs-lookup"><span data-stu-id="55eb1-107">The examples assume that the Arial, Courier New, and Times New Roman fonts are installed in the C:\WINDOWS\Fonts folder on the local computer.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="55eb1-108">この例は、その他のプロパティを定義する方法を示します<xref:System.Windows.Documents.Glyphs>オブジェクト[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="55eb1-108">This example shows how to define other properties of <xref:System.Windows.Documents.Glyphs> objects in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="55eb1-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="55eb1-109">See Also</span></span>  
 [<span data-ttu-id="55eb1-110">WPF のタイポグラフィ</span><span class="sxs-lookup"><span data-stu-id="55eb1-110">Typography in WPF</span></span>](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)
