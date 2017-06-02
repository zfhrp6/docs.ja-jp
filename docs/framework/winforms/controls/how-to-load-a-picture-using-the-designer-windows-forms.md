---
title: "方法 : デザイナーを使用してピクチャを読み込む (Windows フォーム) | Microsoft Docs"
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
  - "フォーム, 表示 (イメージを)"
  - "イメージ [Windows フォーム], 表示 (Windows フォームに)"
  - "ピクチャ形式"
  - "PictureBox コントロール [Windows フォーム], 追加 (ピクチャを)"
  - "ピクチャ, 表示"
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : デザイナーを使用してピクチャを読み込む (Windows フォーム)
Windows フォーム <xref:System.Windows.Forms.PictureBox> コントロールを使用すると、<xref:System.Windows.Forms.PictureBox.Image%2A> プロパティに有効なピクチャを設定することによって、デザイン時にピクチャをフォームに読み込み、表示できます。  受け入れ可能なファイルの種類を次に示します。  
  
|種類|ファイル名の拡張子|  
|--------|---------------|  
|ビットマップ|.bmp|  
|Icon|.ico|  
|GIF|.gif|  
|メタファイル|.wmf|  
|JPEG|.jpg|  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### デザイン時にピクチャを表示するには  
  
1.  フォームに <xref:System.Windows.Forms.PictureBox> コントロールを配置します。  
  
2.  \[プロパティ\] ウィンドウで <xref:System.Windows.Forms.PictureBox.Image%2A> プロパティをクリックします。次に、\[...\] ボタンをクリックして、**\[ファイルを開く\]** ダイアログ ボックスを表示します。  
  
3.  .gif ファイルなど、特定のファイルの種類を検索する場合は、**\[ファイルの種類\]** ボックスでファイルの種類を選択します。  
  
4.  表示するファイルを選択します。  
  
### デザイン時にピクチャを消去するには  
  
1.  **\[プロパティ\]** ウィンドウで <xref:System.Windows.Forms.PictureBox.Image%2A> プロパティを選択し、イメージ オブジェクトの名前の左側に表示されている小さなサムネイル イメージを右クリックします。  **\[リセット\]** を選択します。  
  
## 参照  
 <xref:System.Windows.Forms.PictureBox>   
 [PictureBox コントロールの概要](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)   
 [方法 : 実行時にピクチャのサイズまたは配置を変更する](../../../../docs/framework/winforms/controls/how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)   
 [方法 : 実行時にピクチャを設定する](../../../../docs/framework/winforms/controls/how-to-set-pictures-at-run-time-windows-forms.md)   
 [PictureBox コントロール](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)