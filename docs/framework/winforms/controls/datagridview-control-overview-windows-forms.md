---
title: DataGridView コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- DataGridView
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- grid controls [Windows Forms]
- tables [Windows Forms], displaying in DataGridView control
- tables [Windows Forms], binding to DataGridView control
- columns [Windows Forms], DataGridView control
- bound controls [Windows Forms], dataGridView control
- datasets [Windows Forms], binding to DataGridView control
- data grids [Windows Forms], about data grids
- data [Windows Forms], resorting
- data [Windows Forms], navigating
- grids [Windows Forms]
- data binding [Windows Forms], DataGridView control
- data sources [Windows Forms], binding to DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 0a45c661-89dc-4390-9cc6-c47eee501488
ms.openlocfilehash: 03ba4e13cb014ca03f80781e6630d41c01ae6251
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529965"
---
# <a name="datagridview-control-overview-windows-forms"></a>DataGridView コントロールの概要 (Windows フォーム)
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。 詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 <xref:System.Windows.Forms.DataGridView>コントロールを表示し、さまざまな種類のデータ ソースから表形式のデータを編集できます。  
  
 データをバインドする、<xref:System.Windows.Forms.DataGridView>コントロールは簡単かつ直感的で、および多くの場合は設定などの単純な<xref:System.Windows.Forms.DataGridView.DataSource%2A>プロパティです。 複数のリストまたはテーブルを含むデータ ソースにバインドするときの設定、<xref:System.Windows.Forms.DataGridView.DataMember%2A>プロパティをリストまたはテーブルにバインドするを指定する文字列にします。  
  
 <xref:System.Windows.Forms.DataGridView>コントロールが標準 Windows フォーム データ バインディング モデルをサポートするための次の一覧で説明されているクラスのインスタンスにバインドします。  
  
-   実装するクラス、 <xref:System.Collections.IList> 1 次元配列を含むインターフェイス。  
  
-   実装するクラス、<xref:System.ComponentModel.IListSource>インターフェイスなど、<xref:System.Data.DataTable>と<xref:System.Data.DataSet>クラスです。  
  
-   実装するクラス、<xref:System.ComponentModel.IBindingList>インターフェイスなど、<xref:System.ComponentModel.BindingList%601>クラスです。  
  
-   実装するクラス、<xref:System.ComponentModel.IBindingListView>インターフェイスなど、<xref:System.Windows.Forms.BindingSource>クラスです。  
  
 <xref:System.Windows.Forms.DataGridView>コントロールは、これらのインターフェイスによって返されるオブジェクトのパブリック プロパティまたはによって返されるプロパティのコレクションにデータ バインディングをサポートしている、<xref:System.ComponentModel.ICustomTypeDescriptor>インターフェイスの場合は、返されたオブジェクトに実装します。  
  
 バインドする通常、<xref:System.Windows.Forms.BindingSource>コンポーネントとのバインド、<xref:System.Windows.Forms.BindingSource>コンポーネントを別にデータ ソースまたはビジネス オブジェクトに設定します。 <xref:System.Windows.Forms.BindingSource>コンポーネントが優先されるデータ ソースさまざまなデータ ソースにバインドできる多くのデータ バインドの問題が自動的に解決することができます。 詳細については、次を参照してください。 [BindingSource コンポーネント](../../../../docs/framework/winforms/controls/bindingsource-component.md)です。  
  
 <xref:System.Windows.Forms.DataGridView>コントロールはでも使用できます*バインドされていない*モード、基になるデータ ストアを持たない。 非結合を使用するコード例については<xref:System.Windows.Forms.DataGridView>を制御しを参照してください[チュートリアル: バインドされていない Windows フォーム DataGridView コントロールの作成](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)です。  
  
 <xref:System.Windows.Forms.DataGridView>コントロールが高い構成可能な拡張可能な多くのプロパティ、メソッド、および、外観や動作をカスタマイズするイベントを提供します。 表形式のデータを表示する Windows フォーム アプリケーションを設定する場合は、使用を検討して、<xref:System.Windows.Forms.DataGridView>前に他のユーザー コントロール (たとえば、 <xref:System.Windows.Forms.DataGrid>)。 読み取り専用の値の小さいグリッドを表示する場合、または数百万のレコードを含むテーブルを編集するユーザーを有効にする場合、<xref:System.Windows.Forms.DataGridView>コントロールで、簡単にプログラミング可能なメモリ効率の高いソリューションを提供します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [DataGridView コントロール テクノロジの概要](../../../../docs/framework/winforms/controls/datagridview-control-technology-summary-windows-forms.md)  
 概要を示します<xref:System.Windows.Forms.DataGridView>の概念と、関連するクラスの使用を制御します。  
  
 [DataGridView コントロールのアーキテクチャ](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 アーキテクチャについて説明、<xref:System.Windows.Forms.DataGridView>コントロール、その型の階層と継承構造を説明します。  
  
 [DataGridView コントロールのシナリオ](../../../../docs/framework/winforms/controls/datagridview-control-scenarios-windows-forms.md)  
 これで最も一般的なシナリオについて説明します<xref:System.Windows.Forms.DataGridView>コントロールを使用します。  
  
 [DataGridView コントロールのコード ディレクトリ](../../../../docs/framework/winforms/controls/datagridview-control-code-directory-windows-forms.md)  
 さまざまなドキュメントのコード例へのリンクを提供<xref:System.Windows.Forms.DataGridView>タスク。 コード例はタスクの種類ごとに分類されています。  
  
## <a name="related-sections"></a>関連項目  
 [Windows フォーム DataGridView コントロールの列型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 Windows フォームで列の型について説明します<xref:System.Windows.Forms.DataGridView>コントロールの情報を表示したり変更したり、情報を追加できるようにするために使用します。  
  
 [Windows フォーム DataGridView コントロールでのデータの表示](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 コントロールに手動でデータを組み込む方法と、外部データ ソースからデータを取得する方法について説明するトピックを示します。  
  
 [Windows フォーム DataGridView コントロールのカスタマイズ](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 <xref:System.Windows.Forms.DataGridView> のセルおよび行のカスタム描画と、セル、列、および行の派生型の作成について説明するトピックを示します。  
  
 [Windows フォーム DataGridView コントロールでのパフォーマンス チューニング](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 大量のデータを扱うときのパフォーマンスの問題を避けるために、このコントロールを効率的に使用する方法について説明するトピックを示します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [DataGridView コントロール](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [Windows フォーム DataGridView コントロールの既定の機能](../../../../docs/framework/winforms/controls/default-functionality-in-the-windows-forms-datagridview-control.md)  
 [Windows フォーム DataGridView コントロールの既定のキーボード処理とマウス処理](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
