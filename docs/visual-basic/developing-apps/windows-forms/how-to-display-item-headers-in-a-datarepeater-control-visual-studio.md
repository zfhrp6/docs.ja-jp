---
title: '方法 : DataRepeater コントロールに項目ヘッダーを表示する (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, item headers
- DataRepeater, selection indicators
ms.assetid: 37321447-0ffa-43e1-bdc9-0480e392b90f
ms.openlocfilehash: 07f6a7e06c5b1e91597ab6b6d816407a2c172278
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592140"
---
# <a name="how-to-display-item-headers-in-a-datarepeater-control-visual-studio"></a>方法 : DataRepeater コントロールに項目ヘッダーを表示する (Visual Studio)
項目のヘッダー、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールに視覚インジケーターが用意されて ときに、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>が選択されています。 ときに、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>プロパティに設定されている<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical>(既定)、各項目の左側に項目ヘッダーが表示されます。 ときに、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>プロパティに設定されている<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>、各項目の上部にある項目ヘッダーが表示されます。  
  
 項目ヘッダーがで指定されている色で表示されますが最初にオンの場合、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>プロパティ、および、白の矢印のアイコンが表示されます。  
  
> [!NOTE]
>  設定した場合、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>に<xref:System.Drawing.Color.White%2A>アイテムが最初に選択したときに、選択記号は表示されません。  
  
 ときに、フィールド、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>フォーカス、アイテム ヘッダーの変更の色、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>背景の色と、矢印アイコンの変更を黒にします。 データが変更された場合は、アイテム ヘッダーの鉛筆のアイコンが表示されます。  
  
 既定の幅 (または高さときに、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>プロパティに設定されている<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>) 項目のヘッダーが 15 ピクセルです。 設定して、幅を変更することができます、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>プロパティです。  
  
> [!NOTE]
>  場合、 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> 11 未満である値に設定されて、アイテム ヘッダーのマークは表示されません。  
  
 項目ヘッダーを非表示を設定してできます、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A>プロパティを**False**です。 ときに<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A>に設定されている**False**、項目が選択されていることだけが示されますが、点線の周囲、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>です。  
  
> [!NOTE]
>  監視することによって、独自の選択インジケーターを提供することも、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>のプロパティ、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>で、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>のイベント、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。 詳細については、「<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>」を参照してください。  
  
### <a name="to-change-the-appearance-of-item-headers"></a>項目ヘッダーの外観を変更するには  
  
1.  Windows フォーム デザイナーでの下部の領域を選択して、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。  
  
    > [!NOTE]
    >  コントロールの下の領域を選択する必要があります。 項目テンプレートのセクションを選択した場合、異なる一連のプロパティが [プロパティ] ウィンドウに表示されます。  
  
2.  [プロパティ] ウィンドウで使用して、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>アイテム ヘッダーの色を変更するプロパティです。  
  
    > [!NOTE]
    >  設定した場合、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A>に<xref:System.Drawing.Color.White%2A>アイテムが最初に選択したときに、選択記号は表示されません。  
  
3.  使用して、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A>項目ヘッダーの幅 (または高さ) を変更するプロパティです。  
  
    > [!NOTE]
    >  場合、 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> 11 未満である値に設定されて、アイテム ヘッダーのマークは表示されません。  
  
### <a name="to-hide-item-headers"></a>項目ヘッダーを非表示にするには  
  
1.  Windows フォーム デザイナーでの下部の領域を選択して、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。  
  
    > [!NOTE]
    >  コントロールの下の領域を選択する必要があります。 項目テンプレートのセクションを選択した場合、異なる一連のプロパティが [プロパティ] ウィンドウに表示されます。  
  
2.  [プロパティ] ウィンドウで、設定、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A>プロパティを**False**です。  
  
     内のアイテムの場合に、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>は選択すると、だけが示されますになります、点線の周囲、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>です。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [DataRepeater コントロールの概要](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [方法: DataRepeater コントロールの外観を変更する](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [方法: DataRepeater コントロールのレイアウトを変更する](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [DataRepeater コントロールのトラブルシューティング](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
