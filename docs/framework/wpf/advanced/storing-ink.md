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
# <a name="storing-ink"></a>インクの格納
<xref:System.Windows.Ink.StrokeCollection.Save%2A>メソッドがインクをシリアル化形式 (ISF) としてインクを格納するためのサポートを提供します。 コンス トラクター、<xref:System.Windows.Ink.StrokeCollection>クラスは、インクのデータを読み取るためのサポートを提供します。  
  
## <a name="ink-storage-and-retrieval"></a>インクの格納と取得  
 このセクションで説明を格納およびでインクを取得する方法、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]プラットフォームです。  
  
 次の例は、[名前を付けて保存] ダイアログ ボックスをユーザーに提示し、インクを保存するボタンのクリック イベント ハンドラーを実装する<xref:System.Windows.Controls.InkCanvas>をファイルに出力します。  
  
 [!code-csharp[DigitalInkTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#12)]
 [!code-vb[DigitalInkTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#12)]  
  
 次の例は、ファイルを開く ダイアログ ボックスをユーザーに提示し、インク ファイルから読み取りにボタンのクリック イベント ハンドラーを実装する<xref:System.Windows.Controls.InkCanvas>要素。  
  
 [!code-csharp[DigitalInkTopics#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#13)]
 [!code-vb[DigitalInkTopics#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#13)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.InkCanvas>  
 [Windows Presentation Foundation](../../../../docs/framework/wpf/index.md)
