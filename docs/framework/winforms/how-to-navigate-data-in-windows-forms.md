---
title: '方法 : Windows フォームでデータ間を移動する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cursors [Windows Forms], data sources
- data sources [Windows Forms], Windows Forms
- Windows Forms, navigating
- CurrencyManager class [Windows Forms], navigating Windows Forms data
- data [Windows Forms], navigating
ms.assetid: 97360f7b-b181-4084-966a-4c62518f735b
ms.openlocfilehash: 9572c1234c07c77d5df0c9cd58499faafe460e4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540369"
---
# <a name="how-to-navigate-data-in-windows-forms"></a>方法 : Windows フォームでデータ間を移動する
データ ソースのレコード間を移動する最も簡単な方法は、Windows アプリケーションにバインドする、<xref:System.Windows.Forms.BindingSource>コンポーネント、データ ソースとしへのコントロールのバインドを<xref:System.Windows.Forms.BindingSource>です。 組み込みのナビゲーション メソッドを使用することができますし、<xref:System.Windows.Forms.BindingSource>このような<xref:System.Windows.Forms.BindingSource.MoveNext%2A>、 <xref:System.Windows.Forms.BindingSource.MoveLast%2A>、<xref:System.Windows.Forms.BindingSource.MovePrevious%2A>と<xref:System.Windows.Forms.BindingSource.MoveFirst%2A>です。 これらのメソッドを使用して、調整は、<xref:System.Windows.Forms.BindingSource.Position%2A>と<xref:System.Windows.Forms.BindingSource.Current%2A>のプロパティ、<xref:System.Windows.Forms.BindingSource>適切にします。 項目を検索してそれを設定して、現在のアイテムとして設定することができますも、<xref:System.Windows.Forms.BindingSource.Position%2A>プロパティです。  
  
### <a name="to-increment-the-position-in-a-data-source"></a>データ ソース内の位置をインクリメントするには  
  
1.  設定、<xref:System.Windows.Forms.BindingSource.Position%2A>のプロパティ、<xref:System.Windows.Forms.BindingSource>に移動するレコードの位置にバインドされたデータにします。 使用して次の例を示しています、<xref:System.Windows.Forms.BindingSource.MoveNext%2A>のメソッド、<xref:System.Windows.Forms.BindingSource>増分値を<xref:System.Windows.Forms.BindingSource.Position%2A>プロパティときに、`nextButton`をクリックします。 <xref:System.Windows.Forms.BindingSource>に関連付けられている、`Customers`データセットのテーブル`Northwind`です。  
  
    > [!NOTE]
    >  設定、<xref:System.Windows.Forms.BindingSource.Position%2A>最初と最後のレコードを超える値をプロパティにならない、エラーとして、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]位置を一覧の境界外の値に設定することはできません。 最初と最後のレコードを超えたがあるかどうかを把握するアプリケーションで重要である場合に、データ要素の数を超えるかどうかをテストするためのロジックが含まれます。  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a>末尾または先頭が渡されるかどうかを確認するには  
  
1.  <xref:System.Windows.Forms.BindingSource.PositionChanged> イベントのイベント ハンドラーを作成します。 ハンドラーで提案された位置の値が実際のデータ要素の数を超えているかどうかをテストすることができます。  
  
     次の例では、データの最後の要素に到達するかどうかをテストする方法を示します。 例では、最後の要素でない場合、**次**フォーム上のボタンが無効になっています。  
  
    > [!NOTE]
    >  、コード内を移動する一覧を変更する必要があります再度有効にすることに注意してください、**次** ボタン、ユーザーは、新しいリストの全体の長さを表示ができます。 またを上記<xref:System.Windows.Forms.BindingSource.PositionChanged>、特定のイベント<xref:System.Windows.Forms.BindingSource>イベント処理メソッドに関連するを必要としています。 処理するためのメソッドの例を次に示します、<xref:System.Windows.Forms.BindingSource.PositionChanged>イベント。  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a>項目を検索して、現在のアイテムとして設定するには  
  
1.  現在のアイテムとして設定するレコードを検索します。 こうことを使用して、<xref:System.Windows.Forms.BindingSource.Find%2A>のメソッド、<xref:System.Windows.Forms.BindingSource>してデータ ソースを実装する場合は、<xref:System.ComponentModel.IBindingList>です。 データの例をいくつかは実装するソース<xref:System.ComponentModel.IBindingList>は<xref:System.ComponentModel.BindingList%601>と<xref:System.Data.DataView>です。  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>関連項目  
 [Windows フォームがサポートするデータ ソース](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 [Windows フォーム データ バインドの変更通知](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [データ連結と Windows フォーム](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [Windows フォームでのデータ バインディング](../../../docs/framework/winforms/windows-forms-data-binding.md)
