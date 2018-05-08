---
title: '方法 : ColumnDefinitionsCollections および RowDefinitionsCollections を使用して列と行を操作する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Grid class
- Grid control [WPF], ColumnDefinitionCollection class
- Grid control [WPF], RowDefinitionCollection class
ms.assetid: bfc7160a-45f2-4e17-9961-df414dfb13c5
ms.openlocfilehash: 6ff5ad4825bd9f683d895341dd084c00f68aa27b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-manipulate-columns-and-rows-by-using-columndefinitionscollections-and-rowdefinitionscollections"></a>方法 : ColumnDefinitionsCollections および RowDefinitionsCollections を使用して列と行を操作する
この例のメソッドを使用する方法を示しています、<xref:System.Windows.Controls.ColumnDefinitionCollection>と<xref:System.Windows.Controls.RowDefinitionCollection>クラスを追加する、オフにすると、行または列の内容のカウントなどのアクションを実行します。 たとえば、できます<xref:System.Windows.Controls.ColumnDefinitionCollection.Add%2A>、 <xref:System.Windows.Controls.ColumnDefinitionCollection.Clear%2A>、または<xref:System.Windows.Controls.ColumnDefinitionCollection.Count%2A>に含まれているアイテム、<xref:System.Windows.Controls.ColumnDefinition>または<xref:System.Windows.Controls.RowDefinition>です。  
  
## <a name="example"></a>例  
 次の例を作成、<xref:System.Windows.Controls.Grid>を持つ要素を<xref:System.Windows.FrameworkElement.Name%2A>の`grid1`します。 <xref:System.Windows.Controls.Grid>が含まれています、<xref:System.Windows.Controls.StackPanel>を保持する<xref:System.Windows.Controls.Button>要素、それぞれ別のコレクションの方法で制御します。 クリックすると、 <xref:System.Windows.Controls.Button>、分離コード ファイル内のメソッド呼び出しがアクティブにします。  
  
 [!code-xaml[ColumnDefinitionsGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml#1)]  
  
 この例は、一連のそれぞれに対応する、カスタム メソッドを定義、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>内のイベント、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ファイル。 列と行の数を変更することができます、<xref:System.Windows.Controls.Grid>でいくつかの方法では、これには追加または行と列を削除し、行と列の合計数をカウントします。 防ぐために<xref:System.ArgumentOutOfRangeException>と<xref:System.ArgumentException>例外、エラー チェック機能を使用することができますを<xref:System.Windows.Controls.ColumnDefinitionCollection.RemoveRange%2A>メソッドを提供します。  
  
 [!code-csharp[ColumnDefinitionsGrid#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ColumnDefinitionsGrid/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ColumnDefinitionsGrid#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ColumnDefinitionsGrid/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Controls.ColumnDefinitionCollection>  
 <xref:System.Windows.Controls.RowDefinitionCollection>
