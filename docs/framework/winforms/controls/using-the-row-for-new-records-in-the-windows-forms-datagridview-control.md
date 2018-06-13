---
title: Windows フォーム DataGridView コントロールにおける新規レコード行の使用
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], adding rows for new records
- rows [Windows Forms], new records
- DataGridView control [Windows Forms], data entry
ms.assetid: 6110f1ea-9794-442c-a98a-f104a1feeaf4
ms.openlocfilehash: abf62cc9165d74f6bf183e3df30d9a768c0c537f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540661"
---
# <a name="using-the-row-for-new-records-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールにおける新規レコード行の使用
使用すると、<xref:System.Windows.Forms.DataGridView>アプリケーション内のデータを編集するため、多くの場合、データ ストアに新しい行のデータを追加する機能をユーザーに付与します。 <xref:System.Windows.Forms.DataGridView>コントロールは、最後の行として常に表示されている、新しいレコードの行を指定してこの機能をサポートしています。 行のヘッダーにアスタリスク (*) 記号が付きます。 次のセクションでは、新しいレコードの行でプログラムが有効な場合の考慮事項について説明します。  
  
## <a name="displaying-the-row-for-new-records"></a>新しいレコードの行を表示します。  
 使用して、<xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A>新しいレコードの行を表示するかどうかを示すプロパティです。 このプロパティの既定値は `true` です。  
  
 新しいレコードの行が表示されるデータのバインドの場合の場合、<xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A>コントロールのプロパティと<xref:System.ComponentModel.IBindingList.AllowNew%2A?displayProperty=nameWithType>データ ソースのプロパティが両方とも`true`です。 いずれかの場合`false`その行は表示されません。  
  
## <a name="populating-the-row-for-new-records-with-default-data"></a>既定のデータの新しいレコードの行を設定します。  
 ユーザーが現在の行と新しいレコードの行を選択するとき、<xref:System.Windows.Forms.DataGridView>制御が発生し、<xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>イベント。  
  
 このイベントは、新しいへのアクセスを提供<xref:System.Windows.Forms.DataGridViewRow>既定のデータを新しい行に設定することができます。 詳細については、次を参照してください[する方法: Windows フォーム DataGridView コントロールの新しい行の既定値の指定。](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)  
  
## <a name="the-rows-collection"></a>行のコレクション  
 新しいレコードの行が含まれている、<xref:System.Windows.Forms.DataGridView>コントロールの<xref:System.Windows.Forms.DataGridView.Rows%2A>コレクションが、2 つの点で動作が異なります。  
  
-   新しいレコードの行を削除できません、<xref:System.Windows.Forms.DataGridView.Rows%2A>コレクション プログラムでします。 <xref:System.InvalidOperationException>が、これが試行された場合にスローされます。 また、ユーザーは、新しいレコードの行を削除できません。 <xref:System.Windows.Forms.DataGridViewRowCollection.Clear%2A?displayProperty=nameWithType>メソッドでは、この行からは削除されません、<xref:System.Windows.Forms.DataGridView.Rows%2A>コレクション。  
  
-   新しいレコードに対して行の後に行を追加されません。 <xref:System.InvalidOperationException>これが試行された場合に発生します。 その結果、新しいレコードの行は常に最後の行に、<xref:System.Windows.Forms.DataGridView>コントロール。 メソッドを<xref:System.Windows.Forms.DataGridViewRowCollection>行を追加する —<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>、 <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>、および<xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>— すべてメソッドを呼び出す挿入内部的に新しいレコードの行が存在する場合。  
  
## <a name="visual-customization-of-the-row-for-new-records"></a>新しいレコードに対して行の視覚的なカスタマイズ  
 指定される行に基づいて新しいレコードの行が作成されるとき、<xref:System.Windows.Forms.DataGridView.RowTemplate%2A>プロパティです。 この行に指定されていない任意のセル スタイルは、その他のプロパティから継承されます。 セル スタイルの継承の詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールのセル スタイル](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)です。  
  
 新しいレコードは各セルから取り出したの行内のセルに表示される初期値<xref:System.Windows.Forms.DataGridViewCell.DefaultNewRowValue%2A>プロパティです。 型のセルの<xref:System.Windows.Forms.DataGridViewImageCell>、このプロパティは、プレース ホルダー イメージを返します。 このプロパティを返しますそれ以外の場合、`null`です。 カスタム値を返すには、このプロパティをオーバーライドすることができます。 ただし、これらの初期値に置換できます、<xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>フォーカスが新しいレコードの行を入力するときにイベント ハンドラー。  
  
 矢印またはアスタリスクは、この行のヘッダーの標準的なアイコンがパブリックに公開されていません。 アイコンをカスタマイズする場合は、カスタムを作成する必要があります。<xref:System.Windows.Forms.DataGridViewRowHeaderCell>クラスです。  
  
 標準のアイコンを使用して、<xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>のプロパティ、<xref:System.Windows.Forms.DataGridViewCellStyle>行ヘッダー セルで使用します。 それらを完全に表示するには、十分な領域がない場合は、標準のアイコンは表示されません。  
  
 行ヘッダー セルに設定すると、文字列値が設定されている場合、テキストとアイコンの両方の十分な空き領域がない場合は、アイコンが最初に削除されます。  
  
## <a name="sorting"></a>並べ替え  
 バインドされていないモードで新しいレコードを常に追加の末尾に、 <xref:System.Windows.Forms.DataGridView> 、ユーザーがの内容を並べ替える場合でも、<xref:System.Windows.Forms.DataGridView>です。 ユーザーが、正しい位置に行を並べ替えるために再度並べ替えを適用する必要があります。この動作はに似ていますが、<xref:System.Windows.Forms.ListView>コントロール。  
  
 データのバインドと仮想モードの場合、並べ替えが適用されるときに、カーソル動作は、データ モデルの実装に依存してになります。 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]行が正しい位置にすぐに並べ替えられます。  
  
## <a name="other-notes-on-the-row-for-new-records"></a>新しいレコードの行の他の注意事項  
 設定することはできません、<xref:System.Windows.Forms.DataGridViewRow.Visible%2A>プロパティには、この行の`false`します。 <xref:System.InvalidOperationException>これが試行された場合に発生します。  
  
 新しいレコードの行は、選択されていない状態で常に作成されます。  
  
## <a name="virtual-mode"></a>仮想モード  
 仮想モードを実装している場合は、データ モデルと、行の追加をロールバックする時点で新しいレコードの行が必要なときに追跡する必要があります。 この機能の正確な実装によって異なります、データ モデルとそのトランザクションのセマンティクスの実装など、コミットのスコープがセルまたは行レベルにあるかどうか。 詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールでの仮想モード](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>  
 [Windows フォーム DataGridView コントロールでのデータ入力](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [方法: Windows フォーム DataGridView コントロールの新しい行に既定値を指定する](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)
