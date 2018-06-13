---
title: '方法 : Windows フォーム DataGridView コントロールの編集モードを指定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
ms.openlocfilehash: 5117dfe2e017cf4af1d352fdbf23c6599c0e56a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536274"
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a>方法 : Windows フォーム DataGridView コントロールの編集モードを指定する
既定では、ユーザーが、現在の内容を編集できる<xref:System.Windows.Forms.DataGridView>テキスト ボックスのセルに入力するか、F2 キーを押します。 これにより、セル編集モードで、以下の条件をすべて満たしている場合。  
  
-   基になるデータ ソースは、編集をサポートします。  
  
-   <xref:System.Windows.Forms.DataGridView>制御を有効にします。  
  
-   <xref:System.Windows.Forms.DataGridView.EditMode%2A>プロパティの値が<xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>です。  
  
-   `ReadOnly`セル、行、列、およびコントロールのプロパティは、すべてのセットを`false`です。  
  
 編集モードでは、ユーザーは、セルの値が変更され、セル値は元に戻すには、esc キー、変更をコミットするには ENTER キーを押します。  
  
 構成することができます、<xref:System.Windows.Forms.DataGridView>制御と現在のセルになったらすぐにセルが編集モードに入るようにします。 ENTER キーおよび ESC キーの動作は変更されていないこのケースが、値がコミットまたは元に戻すした後に、セルが編集モードに残ります。 セルまたは f2 キーを押すときにのみユーザーが入力されたときにのみセルが編集モードに切り替わるようにコントロールを構成することもできます。 最後に、セルを防ぐため除くを呼び出すと編集モードに入ることができます、<xref:System.Windows.Forms.DataGridView.BeginEdit%2A>メソッドです。  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a>DataGridView コントロールの編集モードを変更するには  
  
-   設定、<xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>プロパティを適切な<xref:System.Windows.Forms.DataGridViewEditMode>列挙します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
-   <xref:System> アセンブリおよび <xref:System.Windows.Forms> アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>  
 [Windows フォーム DataGridView コントロールでのデータ入力](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)
