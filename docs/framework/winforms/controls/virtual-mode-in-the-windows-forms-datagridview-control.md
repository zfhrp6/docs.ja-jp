---
title: "Windows フォーム DataGridView コントロールでの仮想モード | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "DataGridView コントロール [Windows フォーム], 仮想モード"
ms.assetid: feae5d43-2848-4b1a-8ea7-77085dc415b5
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# Windows フォーム DataGridView コントロールでの仮想モード
仮想モードを使用すると、<xref:System.Windows.Forms.DataGridView> コントロールとカスタム データ キャッシュ間の対話を管理できます。  仮想モードを実装するには、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A> プロパティを `true` に設定し、ここで説明するイベントのうち 1 つ以上のイベントを処理します。  通常、少なくとも `CellValueNeeded` イベントだけは処理します。このイベントにより、コントロールがデータ キャッシュの値を検索できます。  
  
## バインド モードと仮想モード  
 仮想モードは、バインド モードを補完したり、置き換えたりする場合にのみ必要になります。  バインド モードでは、<xref:System.Windows.Forms.DataGridView.DataSource%2A> プロパティを設定すると、コントロールが、指定したソースからデータを自動的に読み込み、ユーザーが行った変更をソースに送り返します。  バインド モードでは、どのバインド列を表示するかを制御できます。並べ替えなどの操作は、通常、データ ソース自体が処理します。  
  
## バインド モードの補完  
 バインド列と共に非バインド列を表示することによって、バインド モードを補完できます。  これは "混合モード" とも呼ばれ、計算値やユーザー インターフェイス \(UI\) コントロールなどの要素を表示するのに役立ちます。  
  
 非バインド列は、データ ソースの外部に存在するので、データ ソースの並べ替え操作で無視されます。  そのため、混合モードでの並べ替えを有効にする場合は、非バインド データをローカル キャッシュで管理し、仮想モードを実装して <xref:System.Windows.Forms.DataGridView> コントロールがキャッシュと対話できるようにする必要があります。  
  
 仮想モードを使用して非バインド列の値を保持する方法の詳細については、<xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A?displayProperty=fullName> プロパティと <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=fullName> クラスのリファレンス トピックに記載されている例を参照してください。  
  
## バインド モードの置換  
 バインド モードがパフォーマンス上のニーズに適合しない場合は、仮想モード イベント ハンドラーを通じて、カスタム キャッシュ内のすべてのデータを管理できます。  たとえば、仮想モードを使用すると、Just\-In\-Time データ読み込み機構を実装できます。この機構では、ネットワーク接続されたデータベースから必要なデータだけを取得することで最適なパフォーマンスを実現します。   これは、低速のネットワーク接続で大量のデータを操作したり、RAM 容量やストレージ領域が制限されたクライアント コンピューターで作業する場合に特に役立ちます。  
  
 Just\-In\-Time のシナリオにおける仮想モードの使用方法の詳細については、「[Windows フォーム DataGridView コントロールでの Just\-In\-Time データ読み込みによる仮想モードの実装](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)」を参照してください。  
  
## 仮想モード イベント  
 データが読み取り専用の場合は、`CellValueNeeded` イベントを処理するだけで済むことがあります。  その他の仮想モード イベントを使用すると、ユーザーによる編集、行の追加と削除、行レベルのトランザクションなど、特定の機能を有効にできます。  
  
 一部の標準 <xref:System.Windows.Forms.DataGridView> イベント \(ユーザーが行を追加または削除したときに発生するイベントや、セル値の編集、解析、検証、または書式指定時に発生するイベントなど\) は、仮想モードでも役立ちます。  また、セルのツールヒント テキスト、セルと行のエラー テキスト、セルと行のショートカット メニュー データ、行の高さデータなど、一般にバインド データ ソースに保存されない値を保持できるようにするイベントも処理できます。  
  
 行レベルのコミット スコープで読み書き両用データを管理するために仮想モードを実装する方法の詳細については、「[チュートリアル : Windows フォーム DataGridView コントロールでの仮想モードの実装](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)」を参照してください。  
  
 セル レベルのコミット スコープで仮想モードを実装する例については、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A> プロパティのリファレンス トピックを参照してください。  
  
 次のイベントは、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A> プロパティが `true` に設定されているときにのみ発生します。  
  
|Event|Description|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.CellValueNeeded>|コントロールが、データ キャッシュからセル値を取得して表示するために使用します。  このイベントは、非バインド列のセルに対してのみ発生します。|  
|<xref:System.Windows.Forms.DataGridView.CellValuePushed>|コントロールが、セルへのユーザー入力をデータ キャッシュにコミットするために使用します。  このイベントは、非バインド列のセルに対してのみ発生します。<br /><br /> <xref:System.Windows.Forms.DataGridView.CellValuePushed> イベント ハンドラーの外部でキャッシュ値を変更したときは、<xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> メソッドを呼び出して、現在値がコントロールで確実に表示されるようにし、現在有効な自動サイズ変更モードを適用します。|  
|<xref:System.Windows.Forms.DataGridView.NewRowNeeded>|コントロールが、データ キャッシュで新しい行が必要かどうかを示すために使用します。|  
|<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>|コントロールが、コミットされていない変更が行に存在するかどうかを判断するために使用します。|  
|<xref:System.Windows.Forms.DataGridView.CancelRowEdit>|コントロールが、行をキャッシュ値に戻す必要があることを示すために使用します。|  
  
 次のイベントは仮想モードで有効ですが、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A> プロパティの設定と無関係に使用できます。  
  
|イベント|Description|  
|----------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.UserDeletingRow><br /><br /> <xref:System.Windows.Forms.DataGridView.UserDeletedRow><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsRemoved><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsAdded>|行が削除または追加されたことを示すためにコントロールが使用します。これに応じて、データ キャッシュを更新できます。|  
|<xref:System.Windows.Forms.DataGridView.CellFormatting><br /><br /> <xref:System.Windows.Forms.DataGridView.CellParsing><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidated><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidated>|コントロールが、表示するセル値の書式を設定し、ユーザー入力を解析および検証するために使用します。|  
|<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>|<xref:System.Windows.Forms.DataGridView.DataSource%2A> プロパティが設定されているとき、または <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> プロパティが `true` であるときに、コントロールがセルのツールヒント テキストを取得するために使用します。<br /><br /> セルのツールヒントは、<xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> プロパティ値が `true` のときにのみ表示されます。|  
|<xref:System.Windows.Forms.DataGridView.CellErrorTextNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowErrorTextNeeded>|<xref:System.Windows.Forms.DataGridView.DataSource%2A> プロパティが設定されているとき、または <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> プロパティが `true` のときに、コントロールがセルまたは行のエラー テキストを取得するために使用します。<br /><br /> セルまたは行のエラー テキストを変更したときは、<xref:System.Windows.Forms.DataGridView.UpdateCellErrorText%2A> メソッドまたは <xref:System.Windows.Forms.DataGridView.UpdateRowErrorText%2A> メソッドを呼び出して、現在の値がコントロールに確実に表示されるようにします。<br /><br /> セルと行のエラー グリフは、<xref:System.Windows.Forms.DataGridView.ShowCellErrors%2A> プロパティと <xref:System.Windows.Forms.DataGridView.ShowRowErrors%2A> プロパティの値が `true` の場合に表示されます。|  
|<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>|コントロールの <xref:System.Windows.Forms.DataGridView.DataSource%2A> プロパティが設定されているとき、または <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> プロパティが `true` のときに、コントロールがセルまたは行の <xref:System.Windows.Forms.ContextMenuStrip> を取得するために使用します。|  
|<xref:System.Windows.Forms.DataGridView.RowHeightInfoNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>|コントロールが、行の高さ情報をデータ キャッシュから取得または保存するために使用します。  キャッシュされた行の高さ情報を <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed> イベント ハンドラーの外部で変更したときは、<xref:System.Windows.Forms.DataGridView.UpdateRowHeightInfo%2A> を呼び出して、現在の値がコントロールに確実に表示されるようにします。|  
  
## 仮想モードで推奨される手順  
 大量のデータを効率的に操作するために仮想モードを実装する場合は、<xref:System.Windows.Forms.DataGridView> コントロール自体も効率よく操作できるようにする必要があります。  セル スタイル、自動サイズ変更、選択、および行の共有の効果的な使い方の詳細については、「[Windows フォーム DataGridView コントロールを拡張するための推奨される手順](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>   
 [Windows フォーム DataGridView コントロールでのパフォーマンス チューニング](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールを拡張するための推奨される手順](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)   
 [チュートリアル : Windows フォーム DataGridView コントロールでの仮想モードの実装](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールでの Just\-In\-Time データ読み込みによる仮想モードの実装](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)