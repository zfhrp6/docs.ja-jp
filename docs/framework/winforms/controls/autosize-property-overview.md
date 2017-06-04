---
title: "AutoSize プロパティの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "サイズの自動調整"
  - "AutoSize プロパティ"
  - "AutoSizeMode プロパティ"
  - "レイアウト [Windows フォーム], AutoSize"
  - "サイズ変更, 自動"
ms.assetid: 62fd82a2-9565-4f65-925b-9d1e66dc4e7d
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# AutoSize プロパティの概要
<xref:System.Windows.Forms.Control.AutoSize%2A> プロパティプロパティを使用することにより、必要に応じて <xref:System.Windows.Forms.Control.PreferredSize%2A> プロパティで指定された値までコントロールのサイズを変更できます。  特定のコントロールのサイズ変更動作を調整するには、`AutoSizeMode` プロパティを設定します。  
  
## AutoSize 動作  
 <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティは、一部のコントロールだけがサポートします。  また、<xref:System.Windows.Forms.Control.AutoSize%2A> プロパティをサポートするコントロールは、`AutoSizeMode` プロパティもサポートします。  
  
 <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティが生成する動作は、コントロールの種類と `AutoSizeMode` プロパティ \(存在する場合\) の値に応じて多少異なります。  このプロパティが生成する標準動作の一覧とその説明を次の表に示します。  
  
|標準動作|Description|  
|----------|-----------------|  
|自動サイズ変更は実行時の機能です。|このプロパティがコントロールを拡大縮小せず、それ以上の効果が無いことを意味します。|  
|コントロールのサイズを変更しても、<xref:System.Windows.Forms.Control.Location%2A> プロパティの値は常に一定です。|コントロールのコンテンツによってコントロールが拡大する場合、コントロールは右下に向かって拡大します。  コントロールは左側に拡大しません。|  
|<xref:System.Windows.Forms.Control.AutoSize%2A> が `true` の場合、<xref:System.Windows.Forms.Control.Dock%2A> プロパティと <xref:System.Windows.Forms.Control.Anchor%2A> プロパティは有効です。|コントロールの <xref:System.Windows.Forms.Control.Location%2A> プロパティの値は、正確な値に調整されます。<br /><br /> **メモ** <xref:System.Windows.Forms.Label> コントロールには、この規則が適用されません。  ドッキングされる <xref:System.Windows.Forms.Label> コントロールの <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティに `true` を設定すると、<xref:System.Windows.Forms.Label> コントロールは伸縮しません。|  
|コントロールの <xref:System.Windows.Forms.Control.MaximumSize%2A> プロパティと <xref:System.Windows.Forms.Control.MinimumSize%2A> プロパティは、そのコントロールの <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティの値とは無関係に常に有効です。|<xref:System.Windows.Forms.Control.MaximumSize%2A> プロパティと <xref:System.Windows.Forms.Control.MinimumSize%2A> プロパティは、<xref:System.Windows.Forms.Control.AutoSize%2A> プロパティの影響を受けません。|  
|既定で設定される最小サイズはありません。|<xref:System.Windows.Forms.Control.AutoSize%2A> に従ってコントロールが縮小するように設定され、コントロールにコンテンツが含まれていない場合、<xref:System.Windows.Forms.Control.Size%2A> プロパティが 0,0 になることを意味します。  この場合、コントロールは 1 つの点に縮小し、簡単に識別できなくなります。|  
|コントロールで <xref:System.Windows.Forms.Control.GetPreferredSize%2A> メソッドを実装していない場合、<xref:System.Windows.Forms.Control.GetPreferredSize%2A> メソッドは、<xref:System.Windows.Forms.Control.Size%2A> プロパティに代入された最後の値を返します。|<xref:System.Windows.Forms.Control.AutoSize%2A> に `true` を設定しても無効であることを意味します。|  
|<xref:System.Windows.Forms.TableLayoutPanel> セル内のコントロールは、その <xref:System.Windows.Forms.Control.MinimumSize%2A> に達するまで、常にセルのサイズに合わせて縮小します。|このサイズは最大サイズとして適用されます。  セルが <xref:System.Windows.Forms.SizeType> 行または列の一部である場合、これは該当しません。|  
  
## AutoSizeMode プロパティ  
 `AutoSizeMode` プロパティでは、既定の <xref:System.Windows.Forms.Control.AutoSize%2A> 動作をより詳細に制御できます。  `AutoSizeMode` プロパティは、コントロールがそのサイズをコンテンツに合わせてどのように調整するかを指定します。  コンテンツは、たとえば <xref:System.Windows.Forms.Button> コントロールの場合はテキスト、コンテナーの場合は子コントロールになります。  
  
 <xref:System.Windows.Forms.AutoSizeMode> の設定と、各設定による動作の説明を次に示します。  
  
|AutoSizeMode の設定|\[動作\]|  
|----------------------|------------|  
|GrowAndShrink|コントロールは拡大または縮小して、コンテンツを包含します。<br /><br /> <xref:System.Windows.Forms.Control.MinimumSize%2A> 値と <xref:System.Windows.Forms.Control.MaximumSize%2A> 値は有効ですが、<xref:System.Windows.Forms.Control.Size%2A> プロパティの現在値は無視されます。<br /><br /> これは、<xref:System.Windows.Forms.Control.AutoSize%2A> プロパティを持ち、`AutoSizeMode` プロパティを持たないコントロールと同じ動作です。|  
|GrowOnly|コントロールは、コンテンツを包含するのに必要な大きさに拡大しますが、<xref:System.Windows.Forms.Control.Size%2A> プロパティで指定された値より縮小しません。<br /><br /> これは、`AutoSizeMode` の既定値です。|  
  
## AutoSize プロパティをサポートするコントロール  
 <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティと `AutoSizeMode` プロパティをサポートするコントロールを次の表に示します。  
  
|AutoSize のサポート|コントロールの型|  
|--------------------|--------------|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティをサポート。<br />-   `AutoSizeMode` プロパティなし。|<xref:System.Windows.Forms.CheckBox><br /><br /> <xref:System.Windows.Forms.DomainUpDown><br /><br /> <xref:System.Windows.Forms.Label><br /><br /> <xref:System.Windows.Forms.LinkLabel><br /><br /> <xref:System.Windows.Forms.MaskedTextBox> \(<xref:System.Windows.Forms.TextBox> ベース\)<br /><br /> <xref:System.Windows.Forms.NumericUpDown><br /><br /> <xref:System.Windows.Forms.RadioButton><br /><br /> <xref:System.Windows.Forms.TextBox><br /><br /> <xref:System.Windows.Forms.TrackBar>|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティをサポート。<br />-   `AutoSizeMode` プロパティをサポート。|<xref:System.Windows.Forms.Button><br /><br /> <xref:System.Windows.Forms.CheckedListBox><br /><br /> <xref:System.Windows.Forms.FlowLayoutPanel><br /><br /> <xref:System.Windows.Forms.Form><br /><br /> <xref:System.Windows.Forms.GroupBox><br /><br /> <xref:System.Windows.Forms.Panel><br /><br /> <xref:System.Windows.Forms.TableLayoutPanel>|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティなし。|<xref:System.Windows.Forms.CheckedListBox><br /><br /> <xref:System.Windows.Forms.ComboBox><br /><br /> <xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DateTimePicker><br /><br /> <xref:System.Windows.Forms.ListBox><br /><br /> <xref:System.Windows.Forms.ListView><br /><br /> <xref:System.Windows.Forms.MaskedTextBox><br /><br /> <xref:System.Windows.Forms.MonthCalendar><br /><br /> <xref:System.Windows.Forms.ProgressBar><br /><br /> <xref:System.Windows.Forms.PropertyGrid><br /><br /> <xref:System.Windows.Forms.RichTextBox><br /><br /> <xref:System.Windows.Forms.SplitContainer><br /><br /> <xref:System.Windows.Forms.TabControl><br /><br /> <xref:System.Windows.Forms.TabPage><br /><br /> <xref:System.Windows.Forms.TreeView><br /><br /> <xref:System.Windows.Forms.WebBrowser><br /><br /> <xref:System.Windows.Forms.ScrollBar>|  
  
## デザイン環境における AutoSize  
 <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティと `AutoSizeMode` プロパティの値に基づく、デザイン時のコントロールのサイズ変更動作を次に示します。  
  
 特定のコントロールが、ユーザーによるサイズ変更が可能な状態にあるかどうかを確認するには、<xref:System.Windows.Forms.Design.ControlDesigner.SelectionRules%2A> プロパティをオーバーライドします。  次の表で、"サイズを変更できません" は <xref:System.Windows.Forms.Design.SelectionRules> のみを意味し、"サイズを変更できます" は <xref:System.Windows.Forms.Design.SelectionRules> と <xref:System.Windows.Forms.Design.SelectionRules> を意味します。  
  
|AutoSize の設定|デザイン時のサイズ変更ジェスチャ|  
|------------------|----------------------|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> \= `true`<br />-   `AutoSizeMode` プロパティなし。|ユーザーは、デザイン時に次のコントロール以外のコントロールのサイズを変更できません。<br /><br /> -   <xref:System.Windows.Forms.TextBox><br />-   <xref:System.Windows.Forms.MaskedTextBox><br />-   <xref:System.Windows.Forms.RichTextBox><br />-   <xref:System.Windows.Forms.TrackBar>|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> \= `true`<br />-   `AutoSizeMode` \= <xref:System.Windows.Forms.AutoSizeMode>|ユーザーは、デザイン時にコントロールのサイズを変更できません。|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> \= `true`<br />-   `AutoSizeMode` \= <xref:System.Windows.Forms.AutoSizeMode>|ユーザーは、デザイン時にコントロールのサイズを変更できます。  <xref:System.Windows.Forms.Control.Size%2A> プロパティが設定されている場合は、ユーザーはコントロールのサイズを拡大することのみ可能です。|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> \= `false`、または <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティが隠されている。|ユーザーは、デザイン時にコントロールのサイズを変更できます。|  
  
> [!NOTE]
>  生産性を最大限に高めるために、Windows フォーム デザイナーは、<xref:System.Windows.Forms.Form> クラスの <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティをシャドウイングします。  デザイン時のフォームは、実際の設定とは無関係に <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティが `false` に設定されているように動作します。  実行時には、特別な調整は行われず、プロパティ設定で指定されたとおりに <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティが適用されます。  
  
## 参照  
 <xref:System.Windows.Forms.Control.AutoSize%2A>   
 <xref:System.Windows.Forms.Control.PreferredSize%2A>   
 <xref:System.Windows.Forms.Control.GetPreferredSize%2A>