---
title: インクの格納
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ISF (Ink Serialized Format)
- storing ink [WPF]
- ink [WPF], storing
- retrieving ink [WPF]
- Ink Serialized Format (ISF)
ms.assetid: a3f6d16b-d682-4680-9965-907332b4d2b8
ms.openlocfilehash: d3d33be5e8b5cf9dd7e32a52dfc258aa934c5c11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546098"
---
# <a name="storing-ink"></a><span data-ttu-id="b1654-102">インクの格納</span><span class="sxs-lookup"><span data-stu-id="b1654-102">Storing Ink</span></span>
<span data-ttu-id="b1654-103"><xref:System.Windows.Ink.StrokeCollection.Save%2A>メソッドがインクをシリアル化形式 (ISF) としてインクを格納するためのサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="b1654-103">The <xref:System.Windows.Ink.StrokeCollection.Save%2A> methods provide support for storing ink as Ink Serialized Format (ISF).</span></span> <span data-ttu-id="b1654-104">コンス トラクター、<xref:System.Windows.Ink.StrokeCollection>クラスは、インクのデータを読み取るためのサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="b1654-104">Constructors for the <xref:System.Windows.Ink.StrokeCollection> class provide support for reading ink data.</span></span>  
  
## <a name="ink-storage-and-retrieval"></a><span data-ttu-id="b1654-105">インクの格納と取得</span><span class="sxs-lookup"><span data-stu-id="b1654-105">Ink Storage and Retrieval</span></span>  
 <span data-ttu-id="b1654-106">このセクションで説明を格納およびでインクを取得する方法、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]プラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="b1654-106">This section discusses how to store and retrieve ink in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] platform.</span></span>  
  
 <span data-ttu-id="b1654-107">次の例は、[名前を付けて保存] ダイアログ ボックスをユーザーに提示し、インクを保存するボタンのクリック イベント ハンドラーを実装する<xref:System.Windows.Controls.InkCanvas>をファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="b1654-107">The following example implements a button-click event handler that presents the user with a File Save dialog box and saves the ink from an <xref:System.Windows.Controls.InkCanvas> out to a file.</span></span>  
  
 [!code-csharp[DigitalInkTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#12)]
 [!code-vb[DigitalInkTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#12)]  
  
 <span data-ttu-id="b1654-108">次の例は、ファイルを開く ダイアログ ボックスをユーザーに提示し、インク ファイルから読み取りにボタンのクリック イベント ハンドラーを実装する<xref:System.Windows.Controls.InkCanvas>要素。</span><span class="sxs-lookup"><span data-stu-id="b1654-108">The following example implements a button-click event handler that presents the user with a File Open dialog box and reads ink from the file into an <xref:System.Windows.Controls.InkCanvas> element.</span></span>  
  
 [!code-csharp[DigitalInkTopics#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#13)]
 [!code-vb[DigitalInkTopics#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="b1654-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="b1654-109">See Also</span></span>  
 <xref:System.Windows.Controls.InkCanvas>  
 [<span data-ttu-id="b1654-110">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="b1654-110">Windows Presentation Foundation</span></span>](../../../../docs/framework/wpf/index.md)
