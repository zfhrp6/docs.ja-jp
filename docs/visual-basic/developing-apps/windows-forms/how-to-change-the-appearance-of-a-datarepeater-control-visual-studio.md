---
title: '方法 : DataRepeater コントロールの外観を変更する (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, customizing
- DataRepeater, changing run time appearance
ms.assetid: 2af6dfce-760b-489e-b863-8da967f315c3
ms.openlocfilehash: 9863d9343ffcecc1e4aae7f6bc16dae39ef76385
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590122"
---
# <a name="how-to-change-the-appearance-of-a-datarepeater-control-visual-studio"></a>方法 : DataRepeater コントロールの外観を変更する (Visual Studio)
外観を変更することができます、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール プロパティの設定によっては、デザイン時または実行時に処理して、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>イベント。  
  
 コントロールの項目テンプレートのセクションを選択すると、デザイン時に設定したプロパティはごとに繰り返されます<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>実行時にします。 外観に関連するプロパティ、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール自体は明らかになった場合にのみ、コンテナーのパーツが左の実行時に表示されます (たとえば場合、<xref:System.Windows.Forms.Control.Padding%2A>を大きな値に設定されます)。  
  
 実行時に、プロパティの外観に関連することができますに基づいて設定条件。 たとえば、スケジューリングのアプリケーションでは、期日の項目がユーザーに警告する項目の背景色を変更する可能性があります。 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>など、条件付きステートメントでプロパティを設定した場合、イベント ハンドラー `If…Then`、使用することも必要があります、`Else`句を条件が満たされないときに、外観を指定します。  
  
### <a name="to-change-the-appearance-at-design-time"></a>デザイン時の外観を変更するには  
  
1.  Windows フォーム デザイナーで、項目テンプレート (上部) の領域を選択、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。  
  
2.  [プロパティ] ウィンドウでプロパティを選択し、値を変更します。 外観に影響する共通のプロパティを含める<xref:System.Windows.Forms.Control.BackColor%2A>、 <xref:System.Windows.Forms.Control.BackgroundImage%2A>、 <xref:System.Windows.Forms.Panel.BorderStyle%2A>、および<xref:System.Windows.Forms.Control.ForeColor%2A>です。  
  
### <a name="to-change-the-appearance-at-run-time"></a>実行時に外観を変更するには  
  
1.  コード エディターで、[イベント] ボックスの一覧の **[DrawItem]** をクリックします。  
  
2.  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> 、イベント ハンドラーのプロパティを設定するコードを追加します。  
  
     [!code-csharp[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="example"></a>例  
 一般的なカスタマイズをいくらか、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールには、表示色を交互を条件に基づくフィールドの色を変更することで、行が含まれます。 次の例では、これらのカスタマイズを実行する方法を示します。 この例があるか、 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Northwind データベースの Products テーブルにバインドされているコントロール。  
  
 [!code-vb[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.vb)]
 [!code-csharp[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.cs)]  
  
 これらのカスタマイズの両方、条件の両方の側のプロパティを設定するコードを提供する必要がありますに注意してください。 指定しない場合、`Else`条件、実行時に予期しない結果が表示されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>  
 [DataRepeater コントロールの概要](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [DataRepeater コントロールのトラブルシューティング](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [方法: DataRepeater コントロールに、バインドされたデータを表示する](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [方法: DataRepeater コントロールに非バインド コントロールを表示する](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [方法: DataRepeater コントロールに項目ヘッダーを表示する](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)
