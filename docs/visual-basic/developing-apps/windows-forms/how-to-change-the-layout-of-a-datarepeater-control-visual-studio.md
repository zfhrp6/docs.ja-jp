---
title: '方法 : DataRepeater コントロールのレイアウトを変更する (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, changing layout style
- DataRepeater, changing orientation
ms.assetid: 33aa8fd5-ac63-4bd0-ba13-8c2ab17e7824
ms.openlocfilehash: fa780ee40171143c17b5bdbda4a97179ed5f2151
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590843"
---
# <a name="how-to-change-the-layout-of-a-datarepeater-control-visual-studio"></a>方法 : DataRepeater コントロールのレイアウトを変更する (Visual Studio)
<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールを垂直方向 (垂直方向にスクロールを項目) または水平方向 (水平方向にスクロールを項目) のいずれかで表示されることができますの向きです。 デザイン時または実行時に印刷の向きを変更するには変更することによって、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>プロパティです。 変更した場合、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>実行時にプロパティをすることもサイズを変更する、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>および子コントロールを再配置します。  
  
> [!NOTE]
>  上のコントロールの位置を変更する場合、 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> 、実行時に呼び出す必要があります、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>と<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>メソッドの先頭と末尾のコントロールが再配置されるコード ブロックにします。  
  
### <a name="to-change-the-layout-at-design-time"></a>デザイン時レイアウトを変更するには  
  
1.  Windows フォーム デザイナーで、選択、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。  
  
    > [!NOTE]
    >  外側の境界線を選択する必要があります、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>上ではなく、コントロールの下の領域内をクリックするコントロール<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>領域。  
  
2.  [プロパティ] ウィンドウで、設定、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>プロパティを<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical>または<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>です。  
  
### <a name="to-change-the-layout-at-run-time"></a>実行時にレイアウトを変更するには  
  
1.  次のコードを追加するボタンまたはメニュー`Click`イベントのハンドラー。  
  
     [!code-csharp[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.vb)]  
  
2.  サイズを変更する例」のセクションで示すようなコードを追加する必要はほとんどの場合、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>および新しい向きに合わせてコントロールを再配置します。  
  
## <a name="example"></a>例  
 次の例に応答する方法を示しています、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged>イベント ハンドラーでイベント。 この例では、ある必要があります、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>という名前のコントロール`DataRepeater1`フォームでその<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>2 つが含まれて<xref:System.Windows.Forms.TextBox>という名前のコントロール`TextBox1`と`TextBox2`です。  
  
 [!code-csharp[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.cs)]
 [!code-vb[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>  
 [DataRepeater コントロールの概要](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [DataRepeater コントロールのトラブルシューティング](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [方法: DataRepeater コントロールの外観を変更する](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
