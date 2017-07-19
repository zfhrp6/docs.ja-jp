---
title: "方法 : ポップアップ ヘルプを表示する | Microsoft Docs"
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
  - "F1 ヘルプ, ダイアログ ボックスで"
  - "フォーム, 表示 (ヘルプを)"
  - "ヘルプ, 追加 (ダイアログ ボックスに)"
  - "ヘルプ, ポップアップ ヘルプ"
  - "HelpProvider コンポーネント [Windows フォーム]"
  - "モーダル ダイアログ ボックス, ポップアップ ヘルプ"
  - "ポップアップ ヘルプ"
  - "Windows フォーム, 表示 (ヘルプを)"
ms.assetid: 218aa81e-e87e-4d67-af05-11627bbdce3b
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : ポップアップ ヘルプを表示する
Windows フォーム上のヘルプを表示する方法の 1 つは、<xref:System.Windows.Forms.Form.HelpButton%2A> プロパティからアクセスできる、タイトル バーの右側にある **\[ヘルプ\]** ボタンを使用することです。  この種類のヘルプの表示は、ダイアログ ボックスでの使用に適しています。  モーダル形式で表示されるダイアログ ボックス \(<xref:System.Windows.Forms.Form.ShowDialog%2A> メソッドを使用\) は、別のウィンドウにフォーカスを移動するときはモーダル ダイアログ ボックスを閉じる必要があるため、外部のヘルプ システムを起動する場合は問題が発生します。  また、**\[ヘルプ\]** ボタンを使用する場合、**\[最小化\]** ボタンや**\[最大化\]** ボタンがタイトル バーに表示されないようにする必要があります。  これは標準のダイアログ ボックスの規約ですが、通常、フォームには **\[最小化\]** ボタンと **\[最大化\]** ボタンがあります。  
  
 また、ポップアップ ヘルプを実装している場合でも、<xref:System.Windows.Forms.HelpProvider> コンポーネントを使用して、コントロールをヘルプ システムのファイルにリンクできることにも注意してください。  詳細については、「[Windows アプリケーションにヘルプを提供する](../../../../docs/framework/winforms/advanced/how-to-provide-help-in-a-windows-application.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### ポップアップ ヘルプを表示するには  
  
1.  [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) コンポーネントをツールボックスからフォームにドラッグします。  
  
     これは、Windows フォーム デザイナーの下部にあるトレイ内に配置されます。  
  
2.  \[プロパティ\] ウィンドウで、<xref:System.Windows.Forms.Form.HelpButton%2A> プロパティを `true` に設定します。  これで、フォームのタイトル バーの右側に疑問符の付いたボタンが表示されます。  
  
3.  <xref:System.Windows.Forms.Form.HelpButton%2A> が表示されるには、フォームの <xref:System.Windows.Forms.Form.MinimizeBox%2A> プロパティと <xref:System.Windows.Forms.Form.MaximizeBox%2A> プロパティを `false` に設定し、<xref:System.Windows.Forms.Form.ControlBox%2A> プロパティを `true` に設定し、<xref:System.Windows.Forms.Form.FormBorderStyle%2A> プロパティを<xref:System.Windows.Forms.FormBorderStyle>、<xref:System.Windows.Forms.FormBorderStyle>、<xref:System.Windows.Forms.FormBorderStyle>、または <xref:System.Windows.Forms.FormBorderStyle> のいずれかの値に設定する必要があります。  
  
4.  フォーム上のヘルプを表示し、\[プロパティ\] ウィンドウのヘルプの文字列を設定するコントロールを選択します。  これは、[ツールヒント](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)のようなウィンドウに表示されるテキストの文字列です。  
  
5.  **F5** キーを押します。  
  
6.  タイトル バーの **\[ヘルプ\]** ボタンをクリックして、ヘルプの文字列を設定したコントロールをクリックします。  
  
## 参照  
 [ツールヒントを使用したコントロールのヘルプ](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)   
 [Windows フォームでのヘルプの統合](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)   
 [Windows フォーム](../../../../docs/framework/winforms/index.md)