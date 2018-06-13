---
title: DataGridView コントロールのシナリオ (Windows フォーム)
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], about data grids
- DataGridView control [Windows Forms], scenarios
ms.assetid: 09a5fd05-3447-47ec-a4ec-6082a2b7f0dd
ms.openlocfilehash: a320b40664e4fe2254109183731db346a5d7d0b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529039"
---
# <a name="datagridview-control-scenarios-windows-forms"></a>DataGridView コントロールのシナリオ (Windows フォーム)
<xref:System.Windows.Forms.DataGridView>コントロール、さまざまなデータ ソースから表形式のデータを表示することができます。 単純な使用方法については、手動で設定できる、<xref:System.Windows.Forms.DataGridView>コントロールから直接データを操作します。 通常、ただし、外部データ ソースにデータを格納してコントロールをバインドして、<xref:System.Windows.Forms.BindingSource>コンポーネントです。  
  
 このトピックでは、いくつかを実行する一般的なシナリオについて説明します、<xref:System.Windows.Forms.DataGridView>コントロール。  
  
## <a name="scenario-1-displaying-small-amounts-of-data"></a>シナリオ 1: 少量のデータを表示します。  
 表示する外部データ ソースにデータを格納する必要はありません、<xref:System.Windows.Forms.DataGridView>コントロール。 少量のデータを扱う場合は、コントロールを設定し、コントロールからデータを操作できます。 これと呼ばれる*バインドされていないモード*です。 詳細については、次を参照してください。[する方法: バインドされていない Windows フォームの DataGridView コントロールの作成](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md)です。  
  
### <a name="scenario-key-points"></a>シナリオの要点  
  
-   モードではバインドされていない、設定コントロール手動でします。  
  
-   バインドされていないモードは、読み取り専用データが少ない場合に特に適しています。  
  
-   バインドされていないモードはスプレッドシート形式または付けますテーブルにも適しています。  
  
## <a name="scenario-2-viewing-and-updating-data-stored-in-an-external-data-source"></a>シナリオ 2: 表示して、外部データ ソースに格納されているデータの更新  
 使用することができます、<xref:System.Windows.Forms.DataGridView>ユーザーから、データベース テーブルまたはビジネス オブジェクトのコレクションなどのデータ ソースに保持されるデータにアクセスできるユーザー インターフェイス (UI) を管理します。 詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールにデータをバインド](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)です。  
  
### <a name="scenario-key-points"></a>シナリオの要点  
  
-   バインドされたモードでは、データ ソースへの接続、データ ソースのプロパティまたはデータベース列に基づく列を自動的に生成し、コントロールを自動的に設定することができます。  
  
-   バインド モードは、ユーザー負荷が高いデータが操作に適しています。 データを表示する形式指定できるし、ユーザー指定のデータは、データ ソースによって予期される形式に解析できます。 ユーザーに警告され、該当するセルを修正できるように、データ エントリ エラーおよびデータベースの制約のエラーの書式設定を検出できます。  
  
-   列の並べ替えなどの追加機能は、固定すること、および並べ替えは、ワークフローに最も便利な方法でデータを表示するユーザーに有効にします。  
  
-   クリップボードのサポートでは、他のアプリケーションにアプリケーションからデータをコピーすることができます。  
  
## <a name="scenario-3-advanced-data"></a>シナリオ 3: 高度なデータ  
 実装することによってコントロールとデータ間の相互作用を管理するには、標準的なデータ バインディング モデルでは取り上げません特別なニーズがあれば、*仮想モード*です。 セルに関する情報と、コントロール要求情報ことのできる 1 つまたは複数のイベント ハンドラーの実装の仮想モード手段を実装することが必要です。  
  
 たとえば、大量のデータを操作する場合、最適な効率性を確保する仮想モードを実装します。 仮想モードも別のデータ ソースから取得した列と共に表示する非バインド列の値を維持するため便利です。  
  
 仮想モードの詳細については、次を参照してください。[チュートリアル: Windows フォーム DataGridView コントロールでの仮想モードを実装する](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)です。  
  
### <a name="scenario-key-points"></a>シナリオの要点  
  
-   仮想モードは、パフォーマンスを微調整する必要がある場合は、非常に大量のデータを表示するために適しています。  
  
## <a name="scenario-4-automatically-resizing-rows-and-columns"></a>シナリオ 4: は、行と列に自動的にサイズ変更  
 定期的に更新されるデータを表示するときに自動的にサイズを変更する行と列のすべてのコンテンツが表示されていることを確認します。 <xref:System.Windows.Forms.DataGridView>コントロールには、有効または無効にする手動によるサイズ変更、特定の時刻では、プログラムでのサイズを変更するのに便利ないくつかのオプションが用意されていますか、自動的にサイズ変更されるたびに、変更をコンテンツします。 詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールのサイズ変更オプション](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)です。  
  
### <a name="scenario-key-points"></a>シナリオの要点  
  
-   手動のサイズを変更すると、セルの高さと幅を調整するユーザーができます。  
  
-   自動サイズ変更するには、セルの内容がクリップされないように、セルのサイズを維持することができます。  
  
-   プログラムによるサイズ変更するには、継続的なサイズの自動調整のパフォーマンスの低下を避けるために特定の時点でのセルのサイズを変更することができます。  
  
## <a name="scenario-5-simple-customization"></a>シナリオ 5: 単純なカスタマイズ  
 <xref:System.Windows.Forms.DataGridView>コントロールには、その基本的な外観と動作を変更するためのさまざまな方法が用意されています。 詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールのセル スタイル](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)です。  
  
### <a name="scenario-key-points"></a>シナリオの要点  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle> オブジェクトを使用して、色、フォント、書式設定、および複数のレベルと、コントロールの個々 の要素の位置情報を提供できます。  
  
-   セル スタイルは、レイヤーし、コードを再利用すること、複数の要素で共有されることができます。  
  
## <a name="scenario-6-advanced-customization"></a>シナリオ 6: 高度なカスタマイズ  
 <xref:System.Windows.Forms.DataGridView>コントロールには、外観や動作をカスタマイズするためのさまざまな方法が用意されています。  
  
### <a name="scenario-key-points"></a>シナリオの要点  
  
-   セルの描画コードを指定することができます。 詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールのセルの外観をカスタマイズ](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)です。  
  
-   独自の行のペイントを使用できます。 たとえば、コンテンツにまたがる複数の列を含む行を作成するこれは、便利です。 詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールで行の外観をカスタマイズ](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)です。  
  
-   セルの外観をカスタマイズする、独自のセルと列のクラスを実装することができます。 詳細については、次を参照してください。[する方法: セルのカスタマイズおよびその動作を拡張すると外観が Windows フォーム DataGridView コントロールで列](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)です。  
  
-   組み込み列の型によって提供されるもの以外のホスト コントロールを独自のセルと列のクラスを実装することができます。 詳細については、次を参照してください。[する方法: Windows フォーム DataGridView セルでホスト コントロール](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 [DataGridView コントロールの概要](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)
