---
title: DataGridView コントロールのアーキテクチャ (Windows フォーム)
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: a9fc1707b1691266d1844c411a08e7e8f35514ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529480"
---
# <a name="datagridview-control-architecture-windows-forms"></a>DataGridView コントロールのアーキテクチャ (Windows フォーム)
<xref:System.Windows.Forms.DataGridView>コントロールとその関連クラスが表示および表形式のデータを編集する用の柔軟で拡張性の高いシステムとして使用するように設計します。 これらのクラスはすべて、<xref:System.Windows.Forms?displayProperty=nameWithType>名前空間、およびそれらのすべてが"DataGridView"プレフィックスを持つという名前です。  
  
## <a name="architecture-elements"></a>アーキテクチャの要素  
 プライマリ<xref:System.Windows.Forms.DataGridView>コンパニオン クラスから派生<xref:System.Windows.Forms.DataGridViewElement>です。 次のオブジェクト モデルを示しています、<xref:System.Windows.Forms.DataGridViewElement>継承階層です。  
  
 ![DataGridViewElement オブジェクト モデル](../../../../docs/framework/winforms/controls/media/datagridviewelement.gif "DataGridViewElement")  
DataGridViewElement オブジェクト モデル  
  
 <xref:System.Windows.Forms.DataGridViewElement>クラスは、親への参照を提供<xref:System.Windows.Forms.DataGridView>制御があり、<xref:System.Windows.Forms.DataGridViewElement.State%2A>プロパティの値の組み合わせを表す値を保持して、<xref:System.Windows.Forms.DataGridViewElementStates>列挙します。  
  
 次のセクションでは、説明、<xref:System.Windows.Forms.DataGridView>コンパニオンさらに詳しくクラスです。  
  
### <a name="datagridviewelementstates"></a>DataGridViewElementStates  
 <xref:System.Windows.Forms.DataGridViewElementStates>列挙には、次の値が含まれています。  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 この列挙体の値をビットごとの論理演算子で結合できるため、<xref:System.Windows.Forms.DataGridViewElement.State%2A>プロパティは、一度に 1 つ以上の状態を表すことができます。 たとえば、<xref:System.Windows.Forms.DataGridViewElement>同時にできる<xref:System.Windows.Forms.DataGridViewElementStates.Frozen>、 <xref:System.Windows.Forms.DataGridViewElementStates.Selected>、および<xref:System.Windows.Forms.DataGridViewElementStates.Visible>です。  
  
### <a name="cells-and-bands"></a>セルとバンド  
 <xref:System.Windows.Forms.DataGridView>コントロールには 2 つの基本的な種類のオブジェクトは構成されています。 セルとバンド。 すべてのセルから派生して、<xref:System.Windows.Forms.DataGridViewCell>基本クラスです。 2 つの種類、バンドの<xref:System.Windows.Forms.DataGridViewColumn>と<xref:System.Windows.Forms.DataGridViewRow>から派生して両方、<xref:System.Windows.Forms.DataGridViewBand>基本クラスです。  
  
 <xref:System.Windows.Forms.DataGridView>コントロールがいくつかのクラスと相互運用するが、最もよく発生<xref:System.Windows.Forms.DataGridViewCell>、 <xref:System.Windows.Forms.DataGridViewColumn>、および<xref:System.Windows.Forms.DataGridViewRow>です。  
  
### <a name="datagridviewcell"></a>DataGridViewCell  
 セルがの相互作用の基本単位、<xref:System.Windows.Forms.DataGridView>です。 セルの中央に表示し、多くの場合、データ エントリはセルを実行します。 セルを使用してアクセスすることができます、<xref:System.Windows.Forms.DataGridViewRow.Cells%2A>のコレクション、<xref:System.Windows.Forms.DataGridViewRow>クラス、およびするが、選択したセルを使用してアクセスできる、<xref:System.Windows.Forms.DataGridView.SelectedCells%2A>のコレクション、<xref:System.Windows.Forms.DataGridView>コントロール。 次のオブジェクト モデルは、この使用法を示していてを示しています、<xref:System.Windows.Forms.DataGridViewCell>継承階層です。  
  
 ![DataGridViewCell オブジェクト モデル](../../../../docs/framework/winforms/controls/media/datagridviewcell.gif "DataGridViewCell")  
DataGridViewCell オブジェクト モデル  
  
 <xref:System.Windows.Forms.DataGridViewCell>型はすべてのセルの種類の派生元となる抽象基本クラスです。 <xref:System.Windows.Forms.DataGridViewCell> その派生型は、Windows フォーム コントロールが一部のホスト Windows フォーム コントロールではありません。 セルの数式で使用できる編集機能は通常、ホストされるコントロールによって処理されます。  
  
 <xref:System.Windows.Forms.DataGridViewCell> オブジェクトは制御されません、独自の外観とペイントの機能と同じ方法で Windows フォーム コントロールとして。 代わりに、<xref:System.Windows.Forms.DataGridView>の外観は、その<xref:System.Windows.Forms.DataGridViewCell>オブジェクト。 対話によって大幅にセルの動作と外観に影響することができます、<xref:System.Windows.Forms.DataGridView>コントロールのプロパティとイベント。 機能を超えているカスタマイズ用の特別な要件がある場合、<xref:System.Windows.Forms.DataGridView>コントロールから派生した独自のクラスを実装する<xref:System.Windows.Forms.DataGridViewCell>またはその子クラスのいずれか。  
  
 次の一覧から派生したクラスを示しています<xref:System.Windows.Forms.DataGridViewCell>:。  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewImageCell>  
  
-   <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
-   カスタムのセル型  
  
### <a name="datagridviewcolumn"></a>DataGridViewColumn  
 スキーマ、<xref:System.Windows.Forms.DataGridView>コントロールのアタッチされたデータ ストアがで表される、<xref:System.Windows.Forms.DataGridView>コントロールの列です。 アクセスすることができます、<xref:System.Windows.Forms.DataGridView>コントロールの列を使用して、<xref:System.Windows.Forms.DataGridView.Columns%2A>コレクション。 使用して、選択した列にアクセスすることができます、<xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>コレクション。 次のオブジェクト モデルは、この使用法を示していてを示しています、<xref:System.Windows.Forms.DataGridViewColumn>継承階層です。  
  
 ![DataGridViewColumn オブジェクト モデル](../../../../docs/framework/winforms/controls/media/datagridviewcolumn.gif "DataGridViewColumn")  
DataGridViewColumn オブジェクト モデル  
  
 一部のキーのセルの種類はある対応する列の種類です。 これらはから派生した、<xref:System.Windows.Forms.DataGridViewColumn>基本クラスです。  
  
 次の一覧から派生したクラスを示しています<xref:System.Windows.Forms.DataGridViewColumn>:。  
  
-   <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
-   カスタムの列型  
  
### <a name="datagridview-editing-controls"></a>DataGridView 編集コントロール  
 通常高度な編集機能をサポートしているセルは、Windows フォーム コントロールから派生したホストされるコントロールを使用します。 これらのコントロールを実装も、<xref:System.Windows.Forms.IDataGridViewEditingControl>インターフェイスです。 次のオブジェクト モデルでは、これらのコントロールの使用方法を示します。  
  
 ![DataGridView コントロールのオブジェクト モデルの編集](../../../../docs/framework/winforms/controls/media/datagridviewediting.gif "DataGridViewEditing")  
DataGridView 編集コントロール オブジェクト モデル  
  
 次の編集コントロールが付いて、<xref:System.Windows.Forms.DataGridView>コントロール。  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 独自の編集コントロールを作成する方法の詳細については、次を参照してください。[する方法: Windows フォーム DataGridView セルでホスト コントロール](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md)です。  
  
 次の表は、セルの種類、列の種類、および編集コントロール間の関係を示します。  
  
|セルの種類|ホストされるコントロール|列の型|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|N/A|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|該当なし|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|該当なし|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|N/A|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a>DataGridViewRow  
 <xref:System.Windows.Forms.DataGridViewRow>するクラスを表示、データからレコードのデータのフィールドを格納、<xref:System.Windows.Forms.DataGridView>コントロールがアタッチされています。 アクセスすることができます、<xref:System.Windows.Forms.DataGridView>コントロールの行を使用して、<xref:System.Windows.Forms.DataGridView.Rows%2A>コレクション。 使用して、選択した行にアクセスすることができます、<xref:System.Windows.Forms.DataGridView.SelectedRows%2A>コレクション。 次のオブジェクト モデルは、この使用法を示していてを示しています、<xref:System.Windows.Forms.DataGridViewRow>継承階層です。  
  
 ![DataGridViewRow オブジェクト モデル](../../../../docs/framework/winforms/controls/media/datagridviewrow.gif "DataGridViewRow")  
DataGridViewRow オブジェクト モデル  
  
 独自の型を派生させることができます、<xref:System.Windows.Forms.DataGridViewRow>クラス、これは通常できませんが必要です。 <xref:System.Windows.Forms.DataGridView>コントロールがいくつかの行に関連するイベントおよびプロパティの動作のカスタマイズをその<xref:System.Windows.Forms.DataGridViewRow>オブジェクト。  
  
 有効にした場合、<xref:System.Windows.Forms.DataGridView>コントロールの<xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A>プロパティ、新しい行を追加するための特別な行は、最後の行として表示されます。 この行の一部である、<xref:System.Windows.Forms.DataGridView.Rows%2A>コレクションも注意が必要な場合がありますの特別な機能を持っています。 詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールで新しいレコードの行を使用して](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)です。  
  
## <a name="see-also"></a>関連項目  
 [DataGridView コントロールの概要](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 [Windows フォーム DataGridView コントロールのカスタマイズ](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [Windows フォーム DataGridView コントロールにおける新規レコード行の使用](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
