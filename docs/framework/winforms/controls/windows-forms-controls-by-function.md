---
title: "Windows フォーム コントロールの機能別一覧 | Microsoft Docs"
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
  - "コントロール [Windows フォーム], 関数による"
  - "Windows フォーム コントロール, 一覧"
  - "Windows フォーム, コントロールの機能別一覧"
ms.assetid: 5e65a6c3-5d6f-480d-beb8-b28f865f07e3
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Windows フォーム コントロールの機能別一覧
Windows フォームには、さまざまな機能を実行するコントロールとコンポーネントがあります。  次の表に、Windows フォームのコントロールとコンポーネントを機能ごとにまとめて示します。  同じ機能を提供するコントロールが複数ある場合は、推奨コントロールを示し、非推奨コントロールについての注釈を付けています。  さらに、非推奨コントロールとそれに対応する推奨コントロールの一覧を独立した表として示します。  
  
> [!NOTE]
>  次の表は、Windows フォームで使用できるすべてのコントロールやコンポーネントを示しているわけではありません。完全な一覧については、「[Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)」を参照してください。  
  
## 推奨されるコントロールとコンポーネント \(機能別\)  
  
|Function|Control|Description|  
|--------------|-------------|-----------------|  
|データの表示|<xref:System.Windows.Forms.DataGridView> コントロール|<xref:System.Windows.Forms.DataGridView> コントロールには、データを表示するための、カスタマイズできるテーブルが用意されています。  <xref:System.Windows.Forms.DataGridView> クラスを使用すると、セル、行、列、罫線をカスタマイズできます。 **Note:**  <xref:System.Windows.Forms.DataGridView> コントロールには、<xref:System.Windows.Forms.DataGrid> コントロールにはない、さまざまな基本機能と高度な機能が用意されています。  詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。|  
|データ バインディングとナビゲーション|<xref:System.Windows.Forms.BindingSource> コンポーネント|同時実行の管理、変更通知などのサービスを提供し、フォーム上のコントロールとデータとのバインディングを単純化します。|  
||<xref:System.Windows.Forms.BindingNavigator> コントロール|フォーム上のデータをナビゲートしたり操作したりするためのツール バー形式のインターフェイスを実現します。|  
|テキストの編集|<xref:System.Windows.Forms.TextBox> コントロール|デザイン時に入力されたテキストを表示します。このテキストは、実行時にユーザーが編集でき、また、プログラムでも変更できます。|  
||<xref:System.Windows.Forms.RichTextBox> コントロール|書式なしテキスト形式または書式付きテキスト \(RTF\) 形式で書式指定されたテキストを表示できます。|  
||<xref:System.Windows.Forms.MaskedTextBox> コントロール|ユーザー入力の形式に制約を適用します。|  
|情報の表示 \(読み取り専用\)|<xref:System.Windows.Forms.Label> コントロール|ユーザーが直接編集できないテキストを表示します。|  
||<xref:System.Windows.Forms.LinkLabel> コントロール|テキストを Web スタイルのリンクとして表示し、ユーザーが特定のテキストをクリックしたときにイベントを発生させます。  通常、このテキストは他のウィンドウまたは Web サイトへのリンクです。|  
||<xref:System.Windows.Forms.StatusStrip> コントロール|フレーム付きの領域を使用してアプリケーションの現在の状態に関する情報を表示します。通常、親フォームの一番下に表示されます。|  
||<xref:System.Windows.Forms.ProgressBar> コントロール|操作の現在の進行状況をユーザー向けに表示します。|  
|Web ページの表示|<xref:System.Windows.Forms.WebBrowser> コントロール|ユーザーがフォーム内で Web ページをナビゲートできるようにします。|  
|一覧からの選択|<xref:System.Windows.Forms.CheckedListBox> コントロール|スクロール可能な項目の一覧を表示します。各項目の横にチェック ボックスが表示されます。|  
||<xref:System.Windows.Forms.ComboBox> コントロール|項目のドロップダウン リストを表示します。|  
||<xref:System.Windows.Forms.DomainUpDown> コントロール|ユーザーが上下の矢印ボタンを使用してスクロールできる、テキスト項目の一覧を表示します。|  
||<xref:System.Windows.Forms.ListBox> コントロール|テキスト項目およびグラフィカル項目 \(アイコン\) の一覧を表示します。|  
||<xref:System.Windows.Forms.ListView> コントロール|4 つの異なるビューのうちの 1 つで項目を表示します。  ビューには、テキストだけ、テキストと小さいアイコン、テキストと大きいアイコン、および詳細ビューがあります。|  
||<xref:System.Windows.Forms.NumericUpDown> コントロール|ユーザーが上下の矢印ボタンを使用してスクロールできる、数値の一覧を表示します。|  
||<xref:System.Windows.Forms.TreeView> コントロール|テキストとオプションのチェック ボックスまたはアイコンから成るノード オブジェクトの階層的なコレクションを表示します。|  
|グラフィックスの表示|<xref:System.Windows.Forms.PictureBox> コントロール|ビットマップやアイコンなどのグラフィカル ファイルをフレーム内に表示します。|  
|グラフィックスの格納|<xref:System.Windows.Forms.ImageList> コントロール|イメージのリポジトリとして機能します。  <xref:System.Windows.Forms.ImageList> コントロールとそれに含まれるイメージは、異なるアプリケーション間で再利用できます。|  
|値の設定|<xref:System.Windows.Forms.CheckBox> コントロール|チェック ボックスとテキストのラベルを表示します。  一般に、オプションの設定に使用されます。|  
||<xref:System.Windows.Forms.CheckedListBox> コントロール|スクロール可能な項目の一覧を表示します。各項目の横にチェック ボックスが表示されます。|  
||<xref:System.Windows.Forms.RadioButton> コントロール|オンまたはオフにできるボタンを表示します。|  
||<xref:System.Windows.Forms.TrackBar> コントロール|ユーザーが目盛り上でつまみを動かして値を設定できるようにします。|  
|日付の設定|<xref:System.Windows.Forms.DateTimePicker> コントロール|ユーザーが日付または時刻を選択できるグラフィカルなカレンダーを表示します。|  
||<xref:System.Windows.Forms.MonthCalendar> コントロール|ユーザーが日付の範囲を選択できるグラフィカルなカレンダーを表示します。|  
|ダイアログ ボックス|<xref:System.Windows.Forms.ColorDialog> コントロール|ユーザーがインターフェイス要素の色を設定できるカラー ピッカー ダイアログ ボックスを表示します。|  
||<xref:System.Windows.Forms.FontDialog> コントロール|ユーザーがフォントとその属性を設定できるダイアログ ボックスを表示します。|  
||<xref:System.Windows.Forms.OpenFileDialog> コントロール|ユーザーがファイルを参照して選択できるダイアログ ボックスを表示します。|  
||<xref:System.Windows.Forms.PrintDialog> コントロール|ユーザーがプリンターを選択してその属性を設定できるダイアログ ボックスを表示します。|  
||<xref:System.Windows.Forms.PrintPreviewDialog> コントロール|<xref:System.Drawing.Printing.PrintDocument> コンポーネントが印刷時にどのように表示されるかを示すダイアログ ボックスを表示します。|  
||<xref:System.Windows.Forms.FolderBrowserDialog> コントロール|ユーザーがフォルダーを参照、作成して最終的に選択するためのダイアログ ボックスを表示します。|  
||<xref:System.Windows.Forms.SaveFileDialog> コントロール|ユーザーがファイルを保存できるダイアログ ボックスを表示します。|  
|メニュー コントロール|<xref:System.Windows.Forms.MenuStrip> コントロール|カスタム メニューを作成します。 **Note:**  <xref:System.Windows.Forms.MenuStrip> は <xref:System.Windows.Forms.MainMenu> コントロールを置き換えるためにデザインされたものです。|  
||<xref:System.Windows.Forms.ContextMenuStrip> コントロール|カスタムのコンテキスト メニューを作成します。 **Note:**  <xref:System.Windows.Forms.ContextMenuStrip> は <xref:System.Windows.Forms.ContextMenu> コントロールを置き換えるためにデザインされたものです。|  
|コマンド|<xref:System.Windows.Forms.Button> コントロール|プロセスの開始、停止、割り込み|  
||<xref:System.Windows.Forms.LinkLabel> コントロール|テキストを Web スタイルのリンクとして表示し、ユーザーが特定のテキストをクリックしたときにイベントを発生させます。  通常、このテキストは他のウィンドウまたは Web サイトへのリンクです。|  
||<xref:System.Windows.Forms.NotifyIcon> コントロール|タスクバーのステータス通知領域に、バックグラウンドで実行中のアプリケーションを示すアイコンを表示します。|  
||<xref:System.Windows.Forms.ToolStrip> コントロール|Microsoft Windows XP、Microsoft Office、Microsoft Internet Explorer、またはカスタムのルック アンド フィールに装備できるツール バーを作成します。このツール バーはテーマを適用しても適用しなくてもよく、オーバーフローと実行時の項目並べ替えをサポートしています。 **Note:**  <xref:System.Windows.Forms.ToolStrip> コントロールは <xref:System.Windows.Forms.ToolBar> コントロールを置き換えるためにデザインされたものです。|  
|ユーザー ヘルプ|<xref:System.Windows.Forms.HelpProvider> コンポーネント|コントロールのポップアップ ヘルプまたはオンライン ヘルプを提供します。|  
||<xref:System.Windows.Forms.ToolTip> コンポーネント|ユーザーがポインターをコントロール上に移動したときに、コントロールの用途についての簡単な説明を表示するポップアップ ウィンドウを表します。|  
|他のコントロールのグループ化|<xref:System.Windows.Forms.Panel> コントロール|ラベルのないスクロール可能なフレームに、コントロールのセットをグループ化します。|  
||<xref:System.Windows.Forms.GroupBox> コントロール|ラベルの付いたスクロールできないフレームに、コントロール \(オプション ボタンなど\) のセットをグループ化します。|  
||<xref:System.Windows.Forms.TabControl> コントロール|グループ化されたオブジェクトを効率的に整理してアクセスするためのタブ付きページを提供します。|  
||<xref:System.Windows.Forms.SplitContainer> コントロール|移動可能なバーによって区切られた 2 つのパネルを表します。 **Note:**  <xref:System.Windows.Forms.SplitContainer> コントロールは <xref:System.Windows.Forms.Splitter> コントロールを置き換えるためにデザインされたものです。|  
||<xref:System.Windows.Forms.TableLayoutPanel> コントロール|内容を行と列から成るグリッドに動的にレイアウトするパネルを表します。|  
||<xref:System.Windows.Forms.FlowLayoutPanel> コントロール|内容を水平または垂直に動的にレイアウトするパネルを表します。|  
|\[オーディオ\]|<xref:System.Media.SoundPlayer> コントロール|.wav 形式のサウンド ファイルを再生します。  サウンドは非同期に読み込みまたは再生できます。|  
  
## 推奨されないコントロールとコンポーネント \(機能別\)  
  
|Function|推奨されないコントロール|推奨されるコントロール|  
|--------------|------------------|-----------------|  
|データの表示|<xref:System.Windows.Forms.DataGrid>|<xref:System.Windows.Forms.DataGridView>|  
|情報の表示 \(読み取り専用コントロール\)|<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|メニュー コントロール|<xref:System.Windows.Forms.ContextMenu>|<xref:System.Windows.Forms.ContextMenuStrip>|  
||<xref:System.Windows.Forms.MainMenu>|<xref:System.Windows.Forms.MenuStrip>|  
|コマンド|<xref:System.Windows.Forms.ToolBar>|<xref:System.Windows.Forms.ToolStrip>|  
||<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|フォームのレイアウト|<xref:System.Windows.Forms.Splitter>|<xref:System.Windows.Forms.SplitContainer>|  
  
## 参照  
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)   
 [.NET Framework を使用したカスタム Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)