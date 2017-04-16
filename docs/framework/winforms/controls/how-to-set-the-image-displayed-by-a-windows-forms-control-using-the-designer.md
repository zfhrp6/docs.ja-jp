---
title: "方法 : デザイナーを使用して Windows フォーム コントロールによって表示されるイメージを設定する | Microsoft Docs"
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
  - "Button コントロール [Windows フォーム], イメージ"
  - "コントロール [Windows フォーム], イメージ"
  - "例 [Windows フォーム], コントロール"
  - "イメージ [Windows フォーム], Windows フォーム コントロール"
  - "設定 (イメージを), Windows フォーム コントロール"
  - "Windows フォーム コントロール, イメージ"
ms.assetid: ae80d07a-e469-4251-90ca-df71f5852454
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法 : デザイナーを使用して Windows フォーム コントロールによって表示されるイメージを設定する
いくつかの Windows フォーム コントロールは、イメージを表示できます。  イメージの例としては、ボタン上のフロッピー ディスクのアイコンが **\[上書き保存\]** コマンドを示すように、コントロールの目的を明確にするアイコンがあります。  また、コントロールに特定の外観を与えるための背景イメージとしてのアイコンもあります。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### コントロールによって表示されるイメージを設定するには  
  
1.  **\[プロパティ\]** ウィンドウで、コントロールの **\[Image\]** または **\[BackgroundImage\]** プロパティを選択し、省略記号ボタン \(  
  
     ![VisualStudioEllipsesButton スクリーンショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")  
  
     \) をクリックして **\[リソースの選択\]** ダイアログ ボックスを表示します。  
  
2.  表示するイメージを選択します。  
  
## 参照  
 <xref:System.Drawing.Image.FromFile%2A>   
 <xref:System.Drawing.Image>   
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>   
 [各 Windows フォーム コントロールのラベル設定とショートカットの作成](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)