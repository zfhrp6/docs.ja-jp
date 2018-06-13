---
title: Windows フォーム DataGridView コントロールでの仮想モード
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], virtual mode
ms.assetid: feae5d43-2848-4b1a-8ea7-77085dc415b5
ms.openlocfilehash: 2e5724da4442bbfcb0928c864f78744b946acc18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541022"
---
# <a name="virtual-mode-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールでの仮想モード
仮想モードでは、間の相互作用を管理することができます、<xref:System.Windows.Forms.DataGridView>コントロールとカスタム データ キャッシュします。 仮想モードを実装するのには、設定、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>プロパティを`true`し、1 つ以上のこのトピックで説明するイベントを処理します。 通常を処理するには、少なくとも、`CellValueNeeded`イベントで、コントロールのルックアップ データ キャッシュ内の値を使用します。  
  
## <a name="bound-mode-and-virtual-mode"></a>バインド モードと仮想モード  
 仮想モードは、補完したりバインド モードを置き換えたりする必要がある場合にのみ必要があります。 バインドのモードでは設定、<xref:System.Windows.Forms.DataGridView.DataSource%2A>プロパティ、およびコントロールを自動的に、指定したソースからデータを読み込み、ユーザーがこれに変更を送信します。 バインドされた列のどれを表示するを制御し、データ ソース自体は通常並べ替えなどの操作を処理します。  
  
## <a name="supplementing-bound-mode"></a>バインド モードを補足します。  
 バインドされた列とバインドされていない列を表示することによって、バインド モードを補うことができます。 これは、「混合モード」とも呼ばれますが、計算値またはユーザー インターフェイス (UI) を制御するなどの処理を表示するために役立ちます。  
  
 バインドされていない列がデータ ソースの外部にあるため、データ ソースの並べ替え操作によって無視されます。 そのため、混在モードでの並べ替えを有効にするとローカル キャッシュ内でバインドされていないデータを管理してくださいさせる仮想モードを実装、<xref:System.Windows.Forms.DataGridView>コントロールとのやり取りします。  
  
 仮想モードを使用して、非バインド列の値を維持する方法の詳細については、例を参照してください、<xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A?displayProperty=nameWithType>プロパティおよび<xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType>クラスのリファレンス トピックです。  
  
## <a name="replacing-bound-mode"></a>バインド モードの置換  
 バインド モードが、パフォーマンスの要件を満たしていない場合は、仮想モードのイベント ハンドラーを使用して、カスタム キャッシュ内のすべてのデータを管理できます。 読み込みのみを取得するメカニズムだけ時間データを実装する仮想モードを使用するなど、ネットワーク上のデータベースからデータが最適なパフォーマンスを必要です。 このシナリオは、大量の低速ネットワーク接続経由でデータや RAM または記憶域スペースの容量が制限されているクライアント コンピューターを操作するときに特に便利です。  
  
 ・ イン タイムのシナリオで仮想モードの使用に関する詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールで Just-In-Time データ読み込みで仮想モードを実装する](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)です。  
  
## <a name="virtual-mode-events"></a>仮想モード イベント  
 データが読み取り専用の場合、`CellValueNeeded`イベントが唯一のイベントを処理する必要があります。 追加の仮想モード イベントでは、ユーザーを編集する、行の追加と削除、および行レベルのトランザクションのような特定の機能を有効にできます。  
  
 標準的な<xref:System.Windows.Forms.DataGridView>イベント (など、ユーザーを追加の行を削除またはセルの値が場合に発生するイベントは、編集、解析、検証、または書式設定されます) の指定は仮想モードで便利です。 セルのツールヒント テキスト、セルと行のエラー テキスト、セルと行のショートカット メニューのデータ、および行の高さデータなど、バインドされたデータ ソースに通常格納されている値を保持できるようにするイベントを処理することもできます。  
  
 行レベルのコミットのスコープを持つ読み取り/書き込みデータを管理する仮想モードの実装の詳細については、次を参照してください。[チュートリアル: Windows フォーム DataGridView コントロールでの仮想モードを実装する](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)です。  
  
 セル レベルのコミットのスコープを持つ仮想モードを実装する例については、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>プロパティの参照トピックです。  
  
 次のイベントにのみ発生するときに、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>プロパティに設定されている`true`です。  
  
|event|説明|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.CellValueNeeded>|コントロールによって表示用のデータ キャッシュから、セルの値を取得するために使用します。 このイベントは、バインドされていない列のセルに対してのみ発生します。|  
|<xref:System.Windows.Forms.DataGridView.CellValuePushed>|セルのユーザー入力をデータ キャッシュにコミットするため、コントロールで使用します。 このイベントは、バインドされていない列のセルに対してのみ発生します。<br /><br /> 呼び出す、<xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A>メソッドの外部のキャッシュされた値を変更するときに、<xref:System.Windows.Forms.DataGridView.CellValuePushed>コントロールで現在の値が表示されていることを確認し、現在有効になっている自動サイズ変更モードを適用するイベント ハンドラー。|  
|<xref:System.Windows.Forms.DataGridView.NewRowNeeded>|データ キャッシュ内の新しい行の必要性を示すために、コントロールで使用します。|  
|<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>|コントロールによって行に確定されていない変更があるかどうかを決定するために使用します。|  
|<xref:System.Windows.Forms.DataGridView.CancelRowEdit>|行は、そのキャッシュされた値に戻すかを示すために、コントロールで使用します。|  
  
 次のイベントは仮想モードでは役立ちますに関係なく使用できます、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>プロパティの設定。  
  
|イベント|説明|  
|------------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.UserDeletingRow><br /><br /> <xref:System.Windows.Forms.DataGridView.UserDeletedRow><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsRemoved><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsAdded>|ときに行が削除またはそれに応じて、データ キャッシュを更新する、追加されたことを示すために、コントロールで使用します。|  
|<xref:System.Windows.Forms.DataGridView.CellFormatting><br /><br /> <xref:System.Windows.Forms.DataGridView.CellParsing><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidated><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidated>|表示用およびを解析し、ユーザー入力を検証するセルの値を書式設定するコントロールで使用します。|  
|<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>|セルのツールヒント テキストを取得するコントロールで使用されるときに、<xref:System.Windows.Forms.DataGridView.DataSource%2A>プロパティが設定または<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>プロパティは`true`します。<br /><br /> セルのツールヒントが表示される場合にのみ、<xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A>プロパティの値が`true`です。|  
|<xref:System.Windows.Forms.DataGridView.CellErrorTextNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowErrorTextNeeded>|セルまたは行のエラー テキストを取得するコントロールで使用されるときに、<xref:System.Windows.Forms.DataGridView.DataSource%2A>プロパティを設定または<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>プロパティは`true`です。<br /><br /> 呼び出す、<xref:System.Windows.Forms.DataGridView.UpdateCellErrorText%2A>メソッドまたは<xref:System.Windows.Forms.DataGridView.UpdateRowErrorText%2A>メソッドは、現在の値がコントロールに表示されるようにセルまたは行のエラー テキストを変更するとします。<br /><br /> セルおよび行のエラー グリフが表示されるときに、<xref:System.Windows.Forms.DataGridView.ShowCellErrors%2A>と<xref:System.Windows.Forms.DataGridView.ShowRowErrors%2A>プロパティの値は`true`します。|  
|<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>|セルまたは行を取得するコントロールで使用される<xref:System.Windows.Forms.ContextMenuStrip>ときにコントロール<xref:System.Windows.Forms.DataGridView.DataSource%2A>プロパティが設定または<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>プロパティは`true`します。|  
|<xref:System.Windows.Forms.DataGridView.RowHeightInfoNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>|データ キャッシュ内の行の高さ情報を格納または取得するコントロールで使用します。 呼び出す、<xref:System.Windows.Forms.DataGridView.UpdateRowHeightInfo%2A>メソッド以外のキャッシュされた行の高さ情報を変更するときに、<xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>イベント ハンドラーを現在の値がコントロールの表示に使用されることを確認してください。|  
  
## <a name="best-practices-in-virtual-mode"></a>仮想モードでのベスト プラクティス  
 大量のデータと効率よく連携するために仮想モードを実装している場合もすることを使用する効率的なことを確認、<xref:System.Windows.Forms.DataGridView>自体を制御します。 セルのスタイル、サイズの自動調整、選択内容、および行の共有の効率的な使用に関する詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールを拡張するためのベスト プラクティス](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 [Windows フォーム DataGridView コントロールでのパフォーマンス チューニング](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [Windows フォーム DataGridView コントロールを拡張するための推奨される手順](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [チュートリアル: Windows フォーム DataGridView コントロールでの仮想モードの実装](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 [Windows フォーム DataGridView コントロールでの Just-In-Time データ読み込みによる仮想モードの実装](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
