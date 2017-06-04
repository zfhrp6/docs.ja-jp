---
title: "組み込みのオーナー描画サポートを備えたコントロール | Microsoft Docs"
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
  - "描画、所有者"
  - "描画、カスタム"
  - "外観を変更するコントロール [Windows フォーム]"
  - "カスタム描画"
  - "オーナー描画"
ms.assetid: 3823d01e-9610-43e6-864d-99f9b7c2b351
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 組み込みのオーナー描画サポートを備えたコントロール
オーナー描画とも呼ばれるカスタムの描画には、Windows フォームでは、特定のコントロールの外観を変更するための手法です。  
  
> [!NOTE]
>  このトピックの「コントロール」という単語はいずれかから派生するクラスを意味するために使用<xref:System.Windows.Forms.Control>または<xref:System.ComponentModel.Component>します。  
  
 通常、Windows の描画を自動的に処理などのプロパティの設定を使用して<xref:System.Windows.Forms.Control.BackColor%2A>コントロールの外観を決定します。 オーナー描画、引き継ぎを行う描画プロセスの外観のプロパティを使用して提供されていない要素を変更します。 たとえば、多くのコントロールを使用して、表示されるテキストの色を設定できますが、1 つの色に制限されます。 オーナー描画では、黒で部分を赤でテキストの一部を表示したりすることができます。  
  
 実際には、オーナー描画は、フォーム上のグラフィックスの描画に似ています。 フォームのため、ハンドラーでグラフィックス メソッドを使用する可能性があります<xref:System.Windows.Forms.Control.Paint>をエミュレートするイベント、`ListBox`コントロールですは、すべてのユーザー操作を処理するコードを記述する必要があります。 オーナー描画、コントロールのサイズ、コードを使用して、その内容を描画するがそれ以外の場合、すべての組み込み機能を保持します。 コントロール内の各項目を描画するか、既定の外観を使用して各項目の他の側面の中に、各項目の一部の機能をカスタマイズするには、グラフィックス メソッドを使用することができます。  
  
## <a name="owner-drawing-in-windows-forms-controls"></a>オーナー描画 Windows フォーム コントロール  
 をサポートしているコントロールのオーナー描画を実行するには、通常&1; つのプロパティを設定して&1; つまたは複数のイベントを処理します。  
  
 ほとんどのコントロールのオーナー描画をサポートしているが、`OwnerDraw`または`DrawMode`コントロールは、描画関連のイベントまたは自身を描画するときにイベントを発生させるかどうかを示すプロパティです。  
  
 コントロールがない、`OwnerDraw`または`DrawMode`プロパティを含む、`DataGridView`コントロールで、自動的に実行する描画イベントを提供するには、および`ToolStrip`を独自の描画に関連するイベントを持つ外部レンダリング クラスを使用して描画するコントロール。  
  
 描画イベントのさまざまな種類がありますが、コントロール内の&1; つの項目を描画するために一般的な描画イベントが発生しました。 イベント ハンドラーは、`EventArgs`を描画することで描画される項目に関する情報を含み、ツール オブジェクトで使用できます。 このオブジェクトが通常、その親コレクション内の項目のインデックス番号を含むなど、<xref:System.Drawing.Rectangle>アイテムの表示の境界を示す、<xref:System.Drawing.Graphics>ペイント メソッドを呼び出すためのオブジェクト。 一部のイベント、`EventArgs`オブジェクトは、アイテムと、バック グラウンドやフォーカス四角形などの既定では、項目の一部の機能の描画に呼び出すことのできるメソッドに関する追加情報を提供します。  
  
 オーナー描画のカスタマイズを含む再利用可能なコントロールを作成するには、オーナー描画をサポートするコントロール クラスから派生する新しいクラスを作成します。 描画イベントを処理するのではなく、オーナー描画コードを適切な上書き含める`On` *EventName*メソッドまたは新しいクラスのメソッドです。 基本クラスを呼び出すことを確認`On` *EventName*メソッドまたはメソッドはここでは、コントロールのユーザーがオーナー描画イベントを処理して、追加のカスタマイズを提供できるようにします。  
  
 次の Windows フォームでは、サポートのオーナー描画、.NET Framework のすべてのバージョンを制御します。  
  
-   <xref:System.Windows.Forms.ListBox>  
  
-   <xref:System.Windows.Forms.ComboBox>  
  
-   <xref:System.Windows.Forms.MenuItem> (で使用される<xref:System.Windows.Forms.MainMenu>と<xref:System.Windows.Forms.ContextMenu>)  
  
-   <xref:System.Windows.Forms.TabControl>  
  
 次のコントロールは、オーナー描画でのみをサポート[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:  
  
-   <xref:System.Windows.Forms.ToolTip>  
  
-   <xref:System.Windows.Forms.ListView>  
  
-   <xref:System.Windows.Forms.TreeView>  
  
 オーナー描画との新機能は次のコントロールがサポート[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:  
  
-   <xref:System.Windows.Forms.DataGridView>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
 次のセクションでは、これらの各コントロールの追加の詳細を説明します。  
  
### <a name="listbox-and-combobox-controls"></a>リスト ボックスやコンボ ボックス コントロール  
 <xref:System.Windows.Forms.ListBox>と<xref:System.Windows.Forms.ComboBox>コントロールを使用すると、すべてに&1; つのサイズまたはさまざまなサイズのいずれかのコントロールに個別の項目を描画します。  
  
> [!NOTE]
>  ですが、 <xref:System.Windows.Forms.CheckedListBox>から派生したコントロールは、 <xref:System.Windows.Forms.ListBox>コントロール、これはサポートされないオーナー描画します。  
  
 同じサイズの各項目を描画する設定、`DrawMode`プロパティを<xref:System.Windows.Forms.DrawMode>を処理し、`DrawItem`イベントです。  
  
 さまざまなサイズを使用して各項目を描画する設定、`DrawMode`プロパティを<xref:System.Windows.Forms.DrawMode>両方を処理し、`MeasureItem`と`DrawItem`イベントです。 `MeasureItem`イベントでは前に、の項目のサイズを指定することができます、`DrawItem`その項目に対してイベントが発生します。  
  
 詳細については、コード例を含む、次のトピックを参照してください。  
  
-   <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=fullName>  
  
-   [方法: ComboBox コントロールに変数のサイズのテキストを作成します。](../../../../docs/framework/winforms/controls/how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a>MenuItem コンポーネント  
 <xref:System.Windows.Forms.MenuItem>コンポーネント内の&1; つのメニュー項目を表す、 <xref:System.Windows.Forms.MainMenu>または<xref:System.Windows.Forms.ContextMenu>コンポーネントです。  
  
 描画する、 <xref:System.Windows.Forms.MenuItem>、設定、`OwnerDraw`プロパティを`true`処理とその`DrawItem`イベントです。 前にメニュー項目のサイズをカスタマイズする、`DrawItem`イベントが発生する処理、項目の`MeasureItem`イベントです。  
  
 詳細については、コード例を含む次のリファレンス トピックを参照してください。  
  
-   <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=fullName>  
  
### <a name="tabcontrol-control"></a>TabControl コントロール  
 <xref:System.Windows.Forms.TabControl>コントロールでは、コントロール内の各タブを描画することができます。 オーナー描画タブのみに影響を与えます<xref:System.Windows.Forms.TabPage>内容が影響を受けません。  
  
 各タブを描画する、 <xref:System.Windows.Forms.TabControl>、設定されて、`DrawMode`プロパティを<xref:System.Windows.Forms.TabDrawMode>を処理し、`DrawItem`イベントです。 タブがコントロールに表示されている場合にのみ、このイベントは各タブに&1; 回発生します。  
  
 詳細については、コード例を含む次のリファレンス トピックを参照してください。  
  
-   <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=fullName>  
  
### <a name="tooltip-component"></a>ToolTip コンポーネント  
 <xref:System.Windows.Forms.ToolTip>コンポーネントでは、表示された場合、全体のツールヒントを描画することができます。  
  
 描画する、<xref:System.Windows.Forms.ToolTip>、設定、`OwnerDraw`プロパティを`true`処理とその`Draw`イベントです。 サイズをカスタマイズする、<xref:System.Windows.Forms.ToolTip>する前に、`Draw`処理イベントが発生する、`Popup`イベントと、 <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A>イベント ハンドラーのプロパティです。  
  
 詳細については、コード例を含む次のリファレンス トピックを参照してください。  
  
-   <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=fullName>  
  
### <a name="listview-control"></a>ListView コントロール  
 <xref:System.Windows.Forms.ListView>コントロールでは、コントロール内の個々 のアイテム、サブ項目、および列ヘッダーを描画することができます。  
  
 コントロールのオーナー描画を有効にするには設定、`OwnerDraw`プロパティを`true`します。  
  
 コントロール内の各項目を描画するには、処理、`DrawItem`イベントです。  
  
 コントロール内の各サブ項目または列ヘッダーを描画するときに、<xref:System.Windows.Forms.ListView.View%2A>にプロパティが設定されている<xref:System.Windows.Forms.View>、処理、`DrawSubItem`と`DrawColumnHeader`イベントです。  
  
 詳細については、コード例を含む次のリファレンス トピックを参照してください。  
  
-   <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=fullName>  
  
### <a name="treeview-control"></a>TreeView コントロール  
 <xref:System.Windows.Forms.TreeView>コントロールでは、コントロール内の個々 のノードを描画することができます。  
  
 各ノードに表示されるテキストのみを描画する設定、`DrawMode`プロパティを<xref:System.Windows.Forms.TreeViewDrawMode>を処理し、`DrawNode`テキストを描画するイベントです。  
  
 各ノードのすべての要素を描画する設定、`DrawMode`プロパティを<xref:System.Windows.Forms.TreeViewDrawMode>を処理し、`DrawNode`ノードを結ぶ線とテキスト、アイコン、チェック ボックス、プラスとマイナス記号 ($) などに必要な任意の要素を描画するイベントです。  
  
 詳細については、コード例を含む次のリファレンス トピックを参照してください。  
  
-   <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=fullName>  
  
### <a name="datagridview-control"></a>DataGridView コントロール  
 <xref:System.Windows.Forms.DataGridView>コントロールでは、コントロール内の個々 のセルおよび行を描画することができます。  
  
 個々 のセルを描画する、`CellPainting`イベントです。  
  
 個々 の行または行の要素を描画する処理の一方または両方、`RowPrePaint`と`RowPostPaint`イベントです。 `RowPrePaint`行内のセルを描画する前に、イベントが発生して、`RowPostPaint`イベント セルが描画された後に発生します。 両方のイベントを処理して、`CellPainting`とは別に、行の背景、個々 のセルおよび行の前景色の描画にイベントまたはするには、場所と必要とするそれらの行の他の要素の既定の表示を使用して特定のカスタマイズを提供できます。  
  
 詳細については、コード例を含む、次のトピックを参照してください。  
  
-   <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
-   [方法: Windows フォーム DataGridView コントロール内のセルの外観をカスタマイズします。](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
  
-   [方法: Windows フォーム DataGridView コントロール内の行の外観をカスタマイズします。](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a>ToolStrip コントロール  
 <xref:System.Windows.Forms.ToolStrip>派生コントロールの外観のさまざまな面をカスタマイズすることを有効にするとします。  
  
 カスタム表示を提供する<xref:System.Windows.Forms.ToolStrip>コントロール、設定、`Renderer`のプロパティ、 <xref:System.Windows.Forms.ToolStrip>、 <xref:System.Windows.Forms.ToolStripManager>、 <xref:System.Windows.Forms.ToolStripPanel>、または<xref:System.Windows.Forms.ToolStripContentPanel>に、`ToolStripRenderer`オブジェクトし、1 つ以上によって提供される多くの描画イベントの処理、`ToolStripRenderer`クラスです。 また、設定、`Renderer`から派生した独自のクラスのインスタンスにプロパティ`ToolStripRenderer`、 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>、または<xref:System.Windows.Forms.ToolStripSystemRenderer>を実装またはオーバーライド特定`On` *EventName*メソッドです。  
  
 詳細については、コード例を含む、次のトピックを参照してください。  
  
-   <xref:System.Windows.Forms.ToolStripRenderer>  
  
-   [方法: 作成し、Windows フォームに ToolStrip コントロールのカスタム レンダラーを設定](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
-   [方法: ToolStrip コントロールをカスタム描画](../../../../docs/framework/winforms/controls/how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a>関連項目  
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)