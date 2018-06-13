---
title: '方法 : DataRepeater コントロールにバインドされたデータを表示する (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, data-binding
- DataRepeater, displaying bound controls
ms.assetid: 56a15326-1334-4275-af4e-075cad79e6f7
ms.openlocfilehash: b96fb33a0dcf80a86d1fcb6e219e5f35b1f7351c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589868"
---
# <a name="how-to-display-bound-data-in-a-datarepeater-control-visual-studio"></a>方法 : DataRepeater コントロールにバインドされたデータを表示する (Visual Studio)
最も一般的な使用、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールは、データベースまたはその他のデータ ソースからバインドされたデータを表示します。  
  
 バインドされたコントロールのほかに静的ラベルや内の各項目に繰り返し表示されるイメージなど、他のコントロールを追加する可能性があります、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。 詳細については、次を参照してください。[する方法: DataRepeater コントロールにバインドされていないコントロールを表示](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)です。  
  
 バインドすることできますも、データ ソースに実行時に設定して、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>プロパティを`True`へのデータ ソースを割り当てると、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A>プロパティです。 この場合、データ ソースとのすべての対話を管理する必要があります。 詳細については、次を参照してください。 [DataRepeater コントロールでの仮想モード](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md)です。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-data-bound-datarepeater"></a>データ バインド DataRepeater を作成するには  
  
1.  ドラッグ、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>から制御、 **Visual Basic PowerPacks**  タブで、**ツールボックス**フォームまたはコンテナー コントロールにします。  
  
2.  サイズにサイズ変更および位置のハンドルをドラッグし、コントロールを配置します。  
  
     コントロールに 2 つの四角形の領域があることに注意してください。 上部の領域は、*項目テンプレート*; 内の各項目のテンプレートに追加されたコントロールは繰り返されます、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>実行時にコントロールです。 下部の領域は、*ビューポート*項目が表示されます。  
  
     またサイズし、コントロール、または項目テンプレートを変更することで位置、**サイズ**と**位置**プロパティ ウィンドウでプロパティです。  
  
3.  **[データ]** メニューの **[データ ソースの表示]** をクリックします。  
  
    > [!NOTE]
    >  場合、**データソース**ウィンドウが空の場合に、データ ソースを追加します。 詳細については、「[新しいデータ ソースの追加](/visualstudio/data-tools/add-new-data-sources)」を参照してください。  
  
4.  **データ ソース**ウィンドウで、最上位ノードをバインドするデータを含むテーブルを選択します。  
  
5.  変更するテーブルのドロップ タイプ`Details` をクリックして`Details`テーブル ノードのドロップダウン リストでします。  
  
6.  テーブル ノードを選択し、項目テンプレート領域の上にドラッグ、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。  
  
     各フィールドのコントロールの種類が表示されますを指定することができます。 詳細については、次を参照してください。[セットのデータ ソース ウィンドウからドラッグしたときに作成する制御](/visualstudio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [DataRepeater コントロールの概要](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [方法: DataRepeater コントロールに非バインド コントロールを表示する](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [方法: 2 つの DataRepeater コントロール (Visual Studio) を使用してマスター/詳細フォームを作成します。](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [方法: DataRepeater コントロールの外観を変更する](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [DataRepeater コントロールのトラブルシューティング](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
