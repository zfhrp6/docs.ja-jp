---
title: '方法 : PriorityBinding を実装する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
ms.openlocfilehash: cf0ed5c2b55358d3a583ac89e307b23b3ab08a9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557759"
---
# <a name="how-to-implement-prioritybinding"></a>方法 : PriorityBinding を実装する
<xref:System.Windows.Data.PriorityBinding> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]のバインドの一覧を指定することによって動作します。 バインディングのリストの順序は、最高の優先度から最も低い優先順位。 最高の優先度のバインドが値を返す場合が正常に処理される際はありませんリスト内の他のバインディングを処理する必要。 最高の優先度のバインドに評価される時間がかかる場合がある可能性があります、優先順位の高いバインドが正常に値を返すまで、正常に値を返す次の最も優先度が使用されます。  
  
## <a name="example"></a>例  
 示すためにどのように<xref:System.Windows.Data.PriorityBinding>の動作、`AsyncDataSource`次の 3 つのプロパティでオブジェクトが作成されました: `FastDP`、`SlowerDP`と`SlowestDP`です。  
  
 Get アクセサー`FastDP`の値を返します、`_fastDP`データ メンバーです。  
  
 Get アクセサー `SlowerDP` 3 秒間の値を返す前に待機する、`_slowerDP`データ メンバーです。  
  
 Get アクセサー`SlowestDP`を 5 秒間の値を返す前に待機する、`_slowestDP`データ メンバーです。  
  
> [!NOTE]
>  この例は、デモンストレーション目的のみで提供されます。 [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)]ガイドライン推奨桁違いフィールド セットよりも低速であるプロパティを定義します。 詳細については、次を参照してください。 [NIB: プロパティとの間の選択とメソッド](http://msdn.microsoft.com/library/55825e8f-7e2e-448a-9505-7217cc91b1af)です。  
  
 [!code-csharp[PriorityBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 <xref:System.Windows.Controls.TextBlock.Text%2A>プロパティ上にバインドされて`AsyncDS`を使用して<xref:System.Windows.Data.PriorityBinding>:  
  
 [!code-xaml[PriorityBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 バインディング エンジンが処理するときに、<xref:System.Windows.Data.Binding>オブジェクト、1 つ目で始まっている<xref:System.Windows.Data.Binding>にバインドされている、`SlowestDP`プロパティです。 ときにこの<xref:System.Windows.Data.Binding>は、処理は返されません、値が正常にため、これがスリープ状態 5 (秒単位) のため、次へ<xref:System.Windows.Data.Binding>要素を処理します。 次<xref:System.Windows.Data.Binding>は正常に完了しなかった値が 3 秒間スリープ状態にあるためです。 バインディング エンジンは、次のステップに移動<xref:System.Windows.Data.Binding>にバインドされている要素、`FastDP`プロパティです。 これは、 <xref:System.Windows.Data.Binding> "高速 Value"の値を返します。 <xref:System.Windows.Controls.TextBlock>値"Fast"が表示されます。  
  
 3 秒が経過した後、 `SlowerDP` "低速 Value"の値を返します。 <xref:System.Windows.Controls.TextBlock> "低速 Value"の値が表示されます。  
  
 5 秒が経過した後、 `SlowestDP` "最も低速な Value"の値を返します。 そのバインディングは、最初に表示されているために、最高の優先順位をでいます。 <xref:System.Windows.Controls.TextBlock> "最も低速な Value"の値が表示されます。  
  
 参照してください<xref:System.Windows.Data.PriorityBinding>については、バインドからの成功の戻り値と見なされます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
