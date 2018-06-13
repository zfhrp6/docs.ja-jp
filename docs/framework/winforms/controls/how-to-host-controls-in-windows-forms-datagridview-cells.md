---
title: '方法 : Windows フォーム DataGridView Cells でコントロールをホストする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], hosting in cells
- DataGridView control [Windows Forms], hosting controls in cells
- cells [Windows Forms], hosting controls
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
ms.openlocfilehash: 730a0677dbc405617c7075402ba0c20dfbd8724d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534048"
---
# <a name="how-to-host-controls-in-windows-forms-datagridview-cells"></a>方法 : Windows フォーム DataGridView Cells でコントロールをホストする
<xref:System.Windows.Forms.DataGridView> コントロールには数種類の列があり、ユーザーはさまざまな方法で値を入力し、編集できます。 ただし、これらの種類の列がデータ入力の要件を満たさない場合は、独自の種類の列を作成して、任意のコントロールをホストするセルを用意できます。 これを作成するには、<xref:System.Windows.Forms.DataGridViewColumn> および <xref:System.Windows.Forms.DataGridViewCell> から派生する各クラスを定義する必要があります。 また、<xref:System.Windows.Forms.Control> から派生し、<xref:System.Windows.Forms.IDataGridViewEditingControl> インターフェイスを実装するクラスを定義する必要もあります。  
  
 予定表の列を作成する方法を次のコード例に示します。 この列のセルは、通常のテキスト ボックスのセルに日付を表示しますが、ユーザーがセルを編集するときには <xref:System.Windows.Forms.DateTimePicker> コントロールが表示されます。 テキスト ボックスの表示機能を再度実装しなくてもすむように、`CalendarCell` クラスは、<xref:System.Windows.Forms.DataGridViewCell> クラスを直接継承するのではなく <xref:System.Windows.Forms.DataGridViewTextBoxCell> クラスから派生します。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridViewCell> や <xref:System.Windows.Forms.DataGridViewColumn> から派生したクラスに新しいプロパティを追加するときは、`Clone` メソッドをオーバーライドし、複製操作時に新しいプロパティをコピーする必要があります。 また、基底クラスの `Clone` メソッドを呼び出して、基底クラスのプロパティを新しいセルまたは列にコピーする必要もあります。  
  
## <a name="example"></a>例  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   System アセンブリおよび System.Windows.Forms アセンブリへの参照。  
  
 コマンドラインからこの例を Visual Basic または Visual c# のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。 この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。  また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 <xref:System.Windows.Forms.DateTimePicker>  
 [Windows フォーム DataGridView コントロールのカスタマイズ](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [DataGridView コントロールのアーキテクチャ](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [Windows フォーム DataGridView コントロールの列型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
