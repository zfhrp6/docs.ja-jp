---
title: '方法: ハイパーリンクに下線を引くかどうかを指定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Hyperlink control type [WPF]
ms.assetid: 3996cfe6-1dac-4835-aeb3-c719ce9cfee5
ms.openlocfilehash: 3d57039d959aa63c031ef467cd2f8398fc3ffd96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544145"
---
# <a name="how-to-specify-whether-a-hyperlink-is-underlined"></a>方法: ハイパーリンクに下線を引くかどうかを指定する
<xref:System.Windows.Documents.Hyperlink>オブジェクトはインライン レベル フロー コンテンツ要素フロー コンテンツ内のハイパーリンクをホストすることができます。 既定では、<xref:System.Windows.Documents.Hyperlink>を使用して、<xref:System.Windows.TextDecoration>下線を表示するオブジェクト。 <xref:System.Windows.TextDecoration> オブジェクトができる処理を要するインスタンスを作成すると、パフォーマンスが多数ある場合に特に<xref:System.Windows.Documents.Hyperlink>オブジェクト。 広範な利用を加えた場合<xref:System.Windows.Documents.Hyperlink>要素、するをお勧めしますように、イベントをトリガーする場合にのみ下線を表示、<xref:System.Windows.ContentElement.MouseEnter>イベント。  
  
 次の例では、"My MSN"リンクの下線は動的 — これ場合のみ表示されます、<xref:System.Windows.ContentElement.MouseEnter>イベントが発生します。  
  
 ![Textdecorations を表示するハイパーリンク](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")  
Textdecorations をで定義されているハイパーリンク  
  
## <a name="example"></a>例  
 次のマークアップのサンプルでは、<xref:System.Windows.Documents.Hyperlink>および下線を使用せずに定義されています。  
  
 [!code-xaml[Performance#PerformanceSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 次のコード サンプルの下線を作成する方法を示しています、<xref:System.Windows.Documents.Hyperlink>上、<xref:System.Windows.ContentElement.MouseEnter>イベント、上で削除し、<xref:System.Windows.ContentElement.MouseLeave>イベント。  
  
 [!code-csharp[Performance#PerformanceSnippet15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml.cs#performancesnippet15)]
 [!code-vb[Performance#PerformanceSnippet15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/hyperlink.xaml.vb#performancesnippet15)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.TextDecoration>  
 <xref:System.Windows.Documents.Hyperlink>  
 [WPF アプリケーションのパフォーマンスの最適化](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [文字の装飾を作成する](../../../../docs/framework/wpf/advanced/how-to-create-a-text-decoration.md)
