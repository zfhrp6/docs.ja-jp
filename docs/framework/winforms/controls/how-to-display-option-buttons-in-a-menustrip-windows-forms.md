---
title: "方法 : MenuStrip にオプション ボタンを表示する (Windows フォーム) | Microsoft Docs"
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
  - "表示 (オプション ボタンを), MenuStrip [Windows フォーム]"
  - "MenuStrip [Windows フォーム], 表示 (オプション ボタンを)"
  - "オプション ボタン [Windows フォーム], 表示 (MenuStrip で)"
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : MenuStrip にオプション ボタンを表示する (Windows フォーム)
オプション ボタン \(ラジオ ボタンとも呼ばれます\) は、チェック ボックスと似ていますが、同時に選択できる項目が 1 つのみという点が異なります。  既定の <xref:System.Windows.Forms.ToolStripMenuItem> クラスにはオプション ボタンの動作はありませんが、チェック ボックスの動作が備わっています。この動作をカスタマイズすると、<xref:System.Windows.Forms.MenuStrip> コントロールのメニュー項目にオプション ボタンの動作を実装できます。  
  
 メニュー項目の <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> プロパティを `true` にすると、クリックによってチェック マークの表示が切り替わる項目になります。  <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> プロパティは、項目の現在の状態を示します。  基本のオプション ボタンの動作を実装するには、いずれかの項目が選択されたときに、直前に選択されていた項目の <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> プロパティを `false` に設定する必要があります。  
  
 次の手順では、<xref:System.Windows.Forms.ToolStripMenuItem> クラスを継承するクラスにこの機能と追加の機能を実装する方法を説明します。  `ToolStripRadioButtonMenuItem` クラスでは、<xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> や <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> などのメンバーをオーバーライドして、オプション ボタンの選択動作と外観を実現します。  さらに、このクラスでは、親項目が選択されていない場合はサブメニューのオプションが無効になるように、<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> プロパティをオーバーライドします。  
  
### オプション ボタンの選択動作を実装するには  
  
1.  <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> プロパティを `true` に初期化して、項目を選択できるようにします。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]  
  
2.  <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> メソッドをオーバーライドして、新しい項目が選択されたときに、直前に選択されていた項目の選択を解除します。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]  
  
3.  <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> メソッドをオーバーライドして、既に選択されている項目をクリックしても選択が解除されないようにします。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]  
  
### オプション ボタン項目の外観を変更するには  
  
1.  <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> メソッドをオーバーライドし、<xref:System.Windows.Forms.RadioButtonRenderer> クラスを使用して既定のチェックマークをオプション ボタンに置き換えます。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]  
  
2.  <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>、<xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>、<xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>、<xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> の各メソッドをオーバーライドして、マウスの状態を追跡し、<xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> メソッドで正しいオプション ボタンの状態が描画されるようにします。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]  
  
### 親項目が選択されていない場合にサブメニューのオプションを無効にするには  
  
1.  <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> プロパティをオーバーライドして、親項目の <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> 値が `true` で <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> 値が `false` の場合に項目が無効になるようにします。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]  
  
2.  <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> メソッドをオーバーライドして、親項目の <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> イベントにサブスクライブします。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]  
  
3.  親項目の <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> イベントのハンドラーで項目を無効にして、新しい有効な状態で表示を更新します。  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]  
  
## 使用例  
 次のコード例では、完全な `ToolStripRadioButtonMenuItem` クラスを作成し、<xref:System.Windows.Forms.Form> クラスと `Program` クラスを使用してオプション ボタンの動作を確認します。  
  
 [!code-csharp[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
 [!code-vb[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   System、System.Drawing、System.Windows.Forms の各アセンブリへの参照。  
  
## 参照  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStripMenuItem>   
 <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.RadioButtonRenderer>   
 [MenuStrip コントロール](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)   
 [方法 : カスタムの ToolStripRenderer を実装する](../../../../docs/framework/winforms/controls/how-to-implement-a-custom-toolstriprenderer.md)