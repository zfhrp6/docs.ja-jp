---
title: "方法 : Windows フォーム上のタブ オーダーを設定する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TabStop"
  - "TabIndex"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "コントロール [Windows フォーム], 設定 (タブ オーダーを)"
  - "タブ オーダー, コントロール (Windows フォームの)"
  - "Windows フォーム コントロール, 設定 (タブ オーダーを)"
  - "Windows フォーム, 設定 (タブ オーダーを)"
ms.assetid: 71fa8e76-0472-414b-ad3c-0f90166e0ad7
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : Windows フォーム上のタブ オーダーを設定する
タブ オーダーとは、ユーザーが **Tab** キーを押して、コントロール間でフォーカスを移動する順序です。  フォームごとに、独自のタブ オーダーを設定できます。  既定では、タブ オーダーはコントロールを作成した順序と同じになります。  タブ オーダーの番号は 0 から始まります。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### コントロールのタブ オーダーを設定するには  
  
1.  **\[表示\]** メニューの **\[タブ オーダー\]** をクリックします。  
  
     フォームのタブ オーダーの選択モードが有効になります。  各コントロールの左上端に、<xref:System.Windows.Forms.Control.TabIndex%2A> プロパティを表す数字が表示されます。  
  
2.  コントロールを順にクリックして、タブ オーダーを設定します。  
  
    > [!NOTE]
    >  タブ オーダーにおけるコントロールの位置は、0 以上の任意の値に設定できます。  重複が発生した場合は、2 つのコントロールの z オーダーが評価され、手前に表示されるコントロールに対して先にタブの移動が行われます。  \(z オーダーは、コントロールの視覚的な階層構造であり、フォームの z 軸 \(奥行\) に沿ってフォームに描かれます。  z オーダーによって、どのコントロールを手前に表示するかを決定します\)。z オーダーの詳細については、「[Windows フォームのオブジェクトの階層構造](../../../../docs/framework/winforms/controls/how-to-layer-objects-on-windows-forms.md)」を参照してください。  
  
3.  設定が終わると、**\[表示\]** メニューの **\[タブ オーダー\]** をもう一度クリックして、タブ オーダー モードを終了します。  
  
    > [!NOTE]
    >  フォーカスを設定できないコントロールは、無効になったコントロールや表示されないコントロールと同様に、<xref:System.Windows.Forms.Control.TabIndex%2A> プロパティが設定されておらず、タブ オーダーに含まれません。  ユーザーが **Tab** キーを押すと、タブ オーダーに含まれないコントロールはスキップされます。  
  
 \[プロパティ\] ウィンドウで、<xref:System.Windows.Forms.Control.TabIndex%2A> プロパティを使用してタブ オーダーを設定することもできます。  コントロールの <xref:System.Windows.Forms.Control.TabIndex%2A> プロパティを設定すると、タブ オーダー内のコントロールの位置を指定できます。  既定では、最初に描画されたコントロールの <xref:System.Windows.Forms.Control.TabIndex%2A> 値が 0 で、次のコントロールの <xref:System.Windows.Forms.Control.TabIndex%2A> 値が 1、というように順に続きます。  
  
 また、既定では、<xref:System.Windows.Forms.GroupBox> コントロールに、独自の整数の <xref:System.Windows.Forms.Control.TabIndex%2A> 値が設定されています。  <xref:System.Windows.Forms.GroupBox> コントロール自体には、実行時にフォーカスを設定できません。  このため、<xref:System.Windows.Forms.GroupBox> 内の各コントロールには、0.0 の値から始まる独自の 10 進数の <xref:System.Windows.Forms.Control.TabIndex%2A> 値が設定されています。  <xref:System.Windows.Forms.GroupBox> コントロールの <xref:System.Windows.Forms.Control.TabIndex%2A> がインクリメントすると、その中のコントロールの値も同様にインクリメントします。  <xref:System.Windows.Forms.Control.TabIndex%2A> 値を 5 から 6 に変更すると、グループの最初のコントロールの <xref:System.Windows.Forms.Control.TabIndex%2A> 値も自動的に 6.0 に変更され、ほかのコントロールの値も同様に順次変更されます。  
  
 また、フォームのさまざまなコントロールから、任意のコントロールのタブ オーダーをスキップできます。  通常、実行時に **Tab** キーを押すと、タブ オーダー内の各コントロールが選択されます。  <xref:System.Windows.Forms.Control.TabStop%2A> プロパティをオフにすると、フォームのコントロールのタブ オーダーをスキップするように設定できます。  
  
#### タブ オーダーからコントロールを削除するには  
  
1.  \[プロパティ\] ウィンドウで、コントロールの <xref:System.Windows.Forms.Control.TabStop%2A> プロパティを `false` に設定します。  
  
     コントロールの <xref:System.Windows.Forms.Control.TabStop%2A> プロパティを `false` に設定すると、タブ オーダーでのコントロールの順序はそのままですが、Tab キーでコントロールを順番に移動するときにコントロールがスキップされます。  
  
    > [!NOTE]
    >  オプション ボタン グループでは、実行時のタブ ストップは 1 回です。  選択したボタン、つまり <xref:System.Windows.Forms.RadioButton.Checked%2A> プロパティを `true` に設定したボタンの場合、<xref:System.Windows.Forms.Control.TabStop%2A> プロパティが自動的に `true` に設定されますが、その他のボタンの <xref:System.Windows.Forms.Control.TabStop%2A> プロパティは `false` に設定されます。  <xref:System.Windows.Forms.RadioButton> コントロールのグループ化の詳細については、「[セットとして機能する Windows フォーム RadioButton コントロールのグループ化](../../../../docs/framework/winforms/controls/how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)」を参照してください。  
  
## 参照  
 [Windows フォーム コントロール](../../../../docs/framework/winforms/controls/index.md)   
 [Windows フォームでのコントロールの配置](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)   
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)   
 [Windows フォーム コントロールの機能別一覧](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)