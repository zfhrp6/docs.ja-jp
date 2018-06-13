---
title: DataRepeater コントロールのトラブルシューティング (Visual Studio)
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, troubleshooting
ms.assetid: c0ab9469-eced-4f52-aa18-4bd8dd4f1a9a
ms.openlocfilehash: 092bbe89bb73a40dee7161f014d40a581b0ddc06
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591899"
---
# <a name="troubleshooting-the-datarepeater-control-visual-studio"></a>DataRepeater コントロールのトラブルシューティング (Visual Studio)
このトピックは、使用している場合に発生する一般的な問題を一覧表示、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。  
  
## <a name="datarepeater-keyboard-and-mouse-events-are-not-raised"></a>DataRepeater キーボードとマウス イベントは発生しません  
 いくつか<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>キーボードとマウスのイベントなどのコントロール イベントは発生しません。 これは仕様に基づく制限事項です。 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール自体は、コンテナーの<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>オブジェクトされ、実行時にアクセスすることはできません。 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>はデザイン時にイベントを公開しません。 そのため、項目をクリックするか、項目にフォーカスがあるときにキーを押して、イベントは発生しません。  
  
 この例外は、<xref:System.Windows.Forms.Control.Padding%2A>プロパティが多数の端を公開するための十分な値、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。 この場合、公開されている余白をクリックし、マウス イベントが発生します。  
  
 この問題を解決するには、追加、<xref:System.Windows.Forms.Panel>コントロールを<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>のセクションで、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>制御、およびコントロールの残りの部分を追加して、<xref:System.Windows.Forms.Panel>です。 コードを追加することができますし、<xref:System.Windows.Forms.Panel>キーボードとマウスのイベントのコントロールのイベント ハンドラー。  
  
## <a name="the-datarepeater-is-partially-hidden-behind-the-binding-navigator"></a>DataRepeater は部分的に隠れてナビゲーターのバインド  
 追加すると、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールをフォームにしてからのデータ バインド コントロールを追加して、**データ ソース** ウィンドウで、<xref:System.Windows.Forms.BindingNavigator>の上にコントロールが表示される、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。 これは、既知の制限事項、**データ ソース**ウィンドウなどの他のコントロールの動作と一貫性がおよび、<xref:System.Windows.Forms.DataGridView>コントロール。  
  
 移動することができます、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>よりも低い、<xref:System.Windows.Forms.BindingNavigator>または、デザイン時に、制御では、次のようなコードを追加、`Load`イベント ハンドラー。  
  
```vb  
DataRepeater1.Top = ProductsBindingNavigator.Height  
```  
  
```csharp  
dataRepeater1.Top = productsBindingNavigator.Height;  
```  
  
## <a name="controls-are-not-displayed-correctly-at-run-time"></a>実行時にコントロールが正しく表示されません。  
 一部のコントロールで、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>期待どおりに実行時にコントロールが表示されない場合があります。 コントロールの複製に使用されるプロセス、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>を<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>すべてのコントロールのすべてのプロパティを必ず確認できることはできません。 非結合を追加する場合など、<xref:System.Windows.Forms.ListBox>コントロールを<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>デザイン時に制御し、設定、 <xref:System.Windows.Forms.ListBox.Items%2A> 、文字列の一覧を使用して、コレクション、<xref:System.Windows.Forms.ListBox>実行時に空になります。 アカウントに、複製プロセスを使用できないため、これは、<xref:System.Windows.Forms.ListBox.Items%2A>プロパティです。  
  
 このなどの問題を修正するで不足しているプロパティを復元することによって、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned>イベントで、既定の複製が完了した後に発生します。 次の例では、修復する方法、<xref:System.Windows.Forms.ListBox.Items%2A>のコレクション、<xref:System.Windows.Forms.ListBox>内の制御、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned>イベント ハンドラー。  
  
 [!code-csharp[VbPowerPacksDataRepeaterItemCloned#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/troubleshooting-the-datarepeater-control-visual-studio_1.cs)]
 [!code-vb[VbPowerPacksDataRepeaterItemCloned#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/troubleshooting-the-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="the-selection-symbol-on-the-item-header-is-missing"></a>項目ヘッダーに選択範囲のシンボルがありません。  
 変更すると、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>項目のヘッダーのプロパティ、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール、いくつかの色がありますが消える選択記号。 変更、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>プロパティが選択記号が表示されなくなったもあります。  
  
 選択記号のサイズと色を変更することはできません。  
  
-   設定した場合、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>に<xref:System.Drawing.Color.White%2A>項目が最初に選択したときに、選択記号は表示されません。  
  
-   設定した場合、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>に<xref:System.Drawing.Color.Black%2A>コントロールが選択されているし、鉛筆のアイコンはコントロールが編集モードのときしか表示されない場合に、選択記号は表示されません。  
  
-   場合、 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> 11 未満である値に設定されて、アイテム ヘッダーのマークは表示されません。  
  
 使用して独自のアイテムのヘッダーと選択シンボルを指定することができます、<xref:System.Windows.Forms.PictureBox>を管理および監視、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>のプロパティ、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>で、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>のイベント、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。 詳細については、「<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [DataRepeater コントロールの概要](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [方法: DataRepeater コントロールに、バインドされたデータを表示する](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [方法: DataRepeater コントロールに非バインド コントロールを表示する](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [方法: DataRepeater コントロールのレイアウトを変更する](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [方法: DataRepeater コントロールの外観を変更する](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [方法: DataRepeater コントロールに項目ヘッダーを表示する](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)  
 [方法: DataRepeater の項目の追加と削除を無効にする](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)  
 [方法: DataRepeater コントロールでデータを検索する](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)  
 [方法: 2 つの DataRepeater コントロール (Visual Studio) を使用してマスター/詳細フォームを作成します。](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)
