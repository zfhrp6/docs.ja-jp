---
title: Windows フォーム コントロールの機能別一覧
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], by function
- Windows Forms, controls by function
- Windows Forms controls, list of
ms.assetid: 5e65a6c3-5d6f-480d-beb8-b28f865f07e3
ms.openlocfilehash: 058a18878b89991bd8124bd69e18476d4f1479d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541578"
---
# <a name="windows-forms-controls-by-function"></a>Windows フォーム コントロールの機能別一覧
Windows フォーム コントロールと多くの機能を実行するコンポーネントを提供します。 次の表には、Windows フォーム コントロールと一般的な機能に合わせてコンポーネントが一覧表示します。 さらに、複数のコントロールが存在する同じ機能を提供、置き換えるコントロールについての注釈を推奨されるコントロールが表示されます。 別の後続のテーブルには、置換対象のコントロールは、対応する推奨と共に一覧表示されます。  
  
> [!NOTE]
>  すべてのコントロールまたは Windows フォームで使用できるコンポーネント、次の表が表示されません。包括的な一覧は、次を参照してください[Windows フォームで使用するコントロール。](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
  
## <a name="recommended-controls-and-components-by-function"></a>推奨されるコントロールとコンポーネント別関数  
  
|関数|コントロール|説明|  
|--------------|-------------|-----------------|  
|データの表示|<xref:System.Windows.Forms.DataGridView> コントロール|<xref:System.Windows.Forms.DataGridView>コントロールでは、データを表示するカスタマイズ可能なテーブルが用意されています。 <xref:System.Windows.Forms.DataGridView>クラスには、セル、行、列、および罫線のカスタマイズができるようにします。 **注:** 、<xref:System.Windows.Forms.DataGridView>コントロールで欠落している多数の基本と高度な機能を提供する、<xref:System.Windows.Forms.DataGrid>コントロール。 詳細については、次を参照してください[の相違点の間で Windows フォームの DataGridView コントロールと DataGrid コントロール。](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)|  
|データのバインドとナビゲーション|<xref:System.Windows.Forms.BindingSource> コンポーネント|通貨の管理、変更通知、およびその他のサービスを提供することでデータをフォームにコントロールのバインドを簡略化します。|  
||<xref:System.Windows.Forms.BindingNavigator> コントロール|移動して、フォーム上のデータを操作するツールバー型インターフェイスを提供します。|  
|テキストの編集|<xref:System.Windows.Forms.TextBox> コントロール|実行時に、ユーザーによって編集したり、プログラムで変更をデザイン時に入力したテキストを表示します。|  
||<xref:System.Windows.Forms.RichTextBox> コントロール|プレーン テキストまたはリッチ テキスト形 (式 RTF) で書式を設定して表示されるテキストを有効にします。|  
||<xref:System.Windows.Forms.MaskedTextBox> コントロール|ユーザー入力の形式を制限します。|  
|情報の表示 (読み取り専用)|<xref:System.Windows.Forms.Label> コントロール|ユーザーが直接編集できないテキストを表示します。|  
||<xref:System.Windows.Forms.LinkLabel> コントロール|Web スタイルのリンクとしてテキストを表示し、ユーザーが特別なテキストをクリックしたときにイベントをトリガーします。 通常、テキストは、別のウィンドウまたは Web サイトにリンクです。|  
||<xref:System.Windows.Forms.StatusStrip> コントロール|親フォームの下部にある通常フレームの領域を使用して、アプリケーションの現在の状態に関する情報を表示します。|  
||<xref:System.Windows.Forms.ProgressBar> コントロール|ユーザーに操作の現在の進行状況を表示します。|  
|Web ページの表示|<xref:System.Windows.Forms.WebBrowser> コントロール|ユーザーがフォーム内で Web ページをナビゲートできるようにします。|  
|一覧から選択|<xref:System.Windows.Forms.CheckedListBox> コントロール|スクロール可能な項目をチェック ボックスの一覧を表示します。|  
||<xref:System.Windows.Forms.ComboBox> コントロール|項目のドロップダウン リストを表示します。|  
||<xref:System.Windows.Forms.DomainUpDown> コントロール|ユーザーが上下ボタンを使用してスクロールできるテキスト項目の一覧を表示します。|  
||<xref:System.Windows.Forms.ListBox> コントロール|テキストとグラフィカルな項目 (アイコン) の一覧を表示します。|  
||<xref:System.Windows.Forms.ListView> コントロール|次の 4 つの異なるビューのいずれかで項目を表示します。 ビューには、テキストのみ、小さなアイコンと共にテキスト、テキストと大きいアイコン、および詳細ビューが含まれます。|  
||<xref:System.Windows.Forms.NumericUpDown> コントロール|ユーザーが上下ボタンを使用してスクロールできる数字の一覧を表示します。|  
||<xref:System.Windows.Forms.TreeView> コントロール|テキストとオプションのチェック ボックスまたはアイコンで構成されるノード オブジェクトの階層のコレクションを表示します。|  
|グラフィックスを表示します。|<xref:System.Windows.Forms.PictureBox> コントロール|フレーム内のビットマップとアイコンなどのグラフィカルなファイルを表示します。|  
|グラフィックスの格納|<xref:System.Windows.Forms.ImageList> コントロール|イメージのリポジトリとして機能します。 <xref:System.Windows.Forms.ImageList> コントロールとが含まれているイメージは、次の 1 つのアプリケーションから再利用できます。|  
|値の設定|<xref:System.Windows.Forms.CheckBox> コントロール|チェック ボックスとテキストのラベルを表示します。 一般にオプションを設定するために使用します。|  
||<xref:System.Windows.Forms.CheckedListBox> コントロール|スクロール可能な項目をチェック ボックスの一覧を表示します。|  
||<xref:System.Windows.Forms.RadioButton> コントロール|オンまたはオフになっていることができます ボタンを表示します。|  
||<xref:System.Windows.Forms.TrackBar> コントロール|スケール沿いの「つまみ」を移動することによって、スケールに値を設定することができます。|  
|日付の設定|<xref:System.Windows.Forms.DateTimePicker> コントロール|日付または時刻を選択するためのグラフィカルなカレンダーを表示します。|  
||<xref:System.Windows.Forms.MonthCalendar> コントロール|日付の範囲を選択できるようにするグラフィカルな予定表を表示します。|  
|ダイアログ ボックス|<xref:System.Windows.Forms.ColorDialog> コントロール|ユーザー インターフェイス要素の色を設定できる色の選択 ダイアログ ボックスが表示されます。|  
||<xref:System.Windows.Forms.FontDialog> コントロール|フォントとその属性を設定するユーザーを許可する ダイアログ ボックスが表示されます。|  
||<xref:System.Windows.Forms.OpenFileDialog> コントロール|移動し、ファイルを選択できるダイアログ ボックスが表示されます。|  
||<xref:System.Windows.Forms.PrintDialog> コントロール|ユーザーがプリンターを選択し、その属性を設定できるようにする ダイアログ ボックスが表示されます。|  
||<xref:System.Windows.Forms.PrintPreviewDialog> コントロール|どのコントロールに表示されるダイアログ ボックスを表示<xref:System.Drawing.Printing.PrintDocument>コンポーネントは、印刷されたときに表示されます。|  
||<xref:System.Windows.Forms.FolderBrowserDialog> コントロール|[参照]、作成、および最終的にフォルダーを選択できるダイアログが表示されます。|  
||<xref:System.Windows.Forms.SaveFileDialog> コントロール|ユーザー ファイルを保存することを許可 ダイアログ ボックスが表示されます。|  
|メニュー コントロール|<xref:System.Windows.Forms.MenuStrip> コントロール|カスタム メニューを作成します。 **注:** 、<xref:System.Windows.Forms.MenuStrip>を交換できるように設計された、<xref:System.Windows.Forms.MainMenu>コントロール。|  
||<xref:System.Windows.Forms.ContextMenuStrip> コントロール|カスタムのコンテキスト メニューを作成します。 **注:** 、<xref:System.Windows.Forms.ContextMenuStrip>を交換できるように設計された、<xref:System.Windows.Forms.ContextMenu>コントロール。|  
|コマンド|<xref:System.Windows.Forms.Button> コントロール|開始、停止、またはプロセスを中断します。|  
||<xref:System.Windows.Forms.LinkLabel> コントロール|Web スタイルのリンクとしてテキストを表示し、ユーザーが特別なテキストをクリックしたときにイベントをトリガーします。 通常、テキストは、別のウィンドウまたは Web サイトにリンクです。|  
||<xref:System.Windows.Forms.NotifyIcon> コントロール|バック グラウンドで実行されているアプリケーションを表すタスク バーの状態通知領域にアイコンを表示します。|  
||<xref:System.Windows.Forms.ToolStrip> コントロール|Microsoft Windows XP、Microsoft Office、Microsoft Internet Explorer、またはカスタムのルック アンド フィールをテーマ、なしとやオーバーフローおよび実行時の並び替えをサポートするツールバーを作成します。 **注:** 、<xref:System.Windows.Forms.ToolStrip>コントロールは、置換するように設計された、<xref:System.Windows.Forms.ToolBar>コントロール。|  
|ユーザー向けヘルプ|<xref:System.Windows.Forms.HelpProvider> コンポーネント|コントロールのポップアップ ヘルプまたはオンライン ヘルプを提供します。|  
||<xref:System.Windows.Forms.ToolTip> コンポーネント|ユーザーがコントロール上にポインターを置いたときに、コントロールの用途の簡単な説明を表示するポップアップ ウィンドウを提供します。|  
|その他のコントロールをグループ化|<xref:System.Windows.Forms.Panel> コントロール|ラベルのない、スクロール可能なフレーム上のコントロールのセットをグループ化します。|  
||<xref:System.Windows.Forms.GroupBox> コントロール|ラベルの付いた、スクロールできないフレームで一連のラジオ ボタン) などのコントロールをグループ化します。|  
||<xref:System.Windows.Forms.TabControl> コントロール|グループ化されたオブジェクトを効率的にタブ付きページを編成およびへのアクセスを提供します。|  
||<xref:System.Windows.Forms.SplitContainer> コントロール|移動可能なバーで区切られた 2 つのパネルを提供します。 **注:** 、<xref:System.Windows.Forms.SplitContainer>コントロールは、置換するように設計された、<xref:System.Windows.Forms.Splitter>コントロール。|  
||<xref:System.Windows.Forms.TableLayoutPanel> コントロール|内容を行と列から成るグリッドに動的にレイアウトするパネルを表します。|  
||<xref:System.Windows.Forms.FlowLayoutPanel> コントロール|水平方向または垂直方向に内容を動的にレイアウトするパネルを表します。|  
|オーディオ|<xref:System.Media.SoundPlayer> コントロール|サウンド .wav 形式のファイルを再生します。 サウンドの読み込みまたは非同期的に再生されることができます。|  
  
## <a name="superseded-controls-and-components-by-function"></a>コントロールおよびコンポーネント関数によって置き換えられる  
  
|関数|置き換えられるコントロール|推奨される置換|  
|--------------|------------------------|-----------------------------|  
|データの表示|<xref:System.Windows.Forms.DataGrid>|<xref:System.Windows.Forms.DataGridView>|  
|情報の表示 (読み取り専用コントロール)|<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|メニュー コントロール|<xref:System.Windows.Forms.ContextMenu>|<xref:System.Windows.Forms.ContextMenuStrip>|  
||<xref:System.Windows.Forms.MainMenu>|<xref:System.Windows.Forms.MenuStrip>|  
|コマンド|<xref:System.Windows.Forms.ToolBar>|<xref:System.Windows.Forms.ToolStrip>|  
||<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|フォームのレイアウト|<xref:System.Windows.Forms.Splitter>|<xref:System.Windows.Forms.SplitContainer>|  
  
## <a name="see-also"></a>関連項目  
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [.NET Framework を使用したカスタム Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
