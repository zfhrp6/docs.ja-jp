---
title: '方法 : Windows フォーム DataGridView コントロールのボタン列にあるボタンを無効にする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], disabling buttons
- buttons [Windows Forms], disabling in button columns
- DataGridView control [Windows Forms], disabling button cells
ms.assetid: 5c344d01-013a-4a6b-8f8d-62ec9321d81e
ms.openlocfilehash: 957d5ebac7c8f6d7c1f4ce95e79e1918164db955
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-disable-buttons-in-a-button-column-in-the-windows-forms-datagridview-control"></a>方法 : Windows フォーム DataGridView コントロールのボタン列にあるボタンを無効にする
<xref:System.Windows.Forms.DataGridView> コントロールには、ボタンのようなユーザー インターフェイス (UI) を持つセルを表示するための <xref:System.Windows.Forms.DataGridViewButtonCell> クラスが含まれます。 ただし、<xref:System.Windows.Forms.DataGridViewButtonCell> はセルによって表示されるボタンの外観を無効にする方法は提供しません。  
  
 次のコード例は、<xref:System.Windows.Forms.DataGridViewButtonCell> クラスをカスタマイズして表示可能で無効になっているボタンを表示する方法を示しています。 この例は、<xref:System.Windows.Forms.DataGridViewButtonCell> から派生した新しいセルの種類 `DataGridViewDisableButtonCell` を定義します。 このセルの種類は、`false` に設定して無効になっているボタンをセルに描画する提供できる新しい `Enabled` プロパティを提供します。 例は、`DataGridViewDisableButtonCell` オブジェクトを表示する、新しい列の種類である `DataGridViewDisableButtonColumn` も定義します。 この新しいセルと列の種類を示すために、親の <xref:System.Windows.Forms.DataGridView> 内の各 <xref:System.Windows.Forms.DataGridViewCheckBoxCell> の現在値が、同じ行にある`DataGridViewDisableButtonCell` の `Enabled` プロパティが `true` と `false` のいずれであるかを決定します。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridViewCell> や <xref:System.Windows.Forms.DataGridViewColumn> から派生したクラスに新しいプロパティを追加するときは、`Clone` メソッドをオーバーライドし、複製操作時に新しいプロパティをコピーする必要があります。 また、基底クラスの `Clone` メソッドを呼び出して、基底クラスのプロパティを新しいセルまたは列にコピーする必要もあります。  
  
## <a name="example"></a>例  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System、System.Drawing、System.Windows.Forms、および System.Windows.Forms.VisualStyles の各アセンブリへの参照。  
  
 コマンドラインからこの例を Visual Basic または Visual c# のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。 この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。  また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。  
  
## <a name="see-also"></a>関連項目  
 [Windows フォーム DataGridView コントロールのカスタマイズ](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [DataGridView コントロールのアーキテクチャ](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [Windows フォーム DataGridView コントロールの列型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
