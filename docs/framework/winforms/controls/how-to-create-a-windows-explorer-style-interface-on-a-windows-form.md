---
title: "方法 : Windows フォームで Windows エクスプローラー スタイルのインターフェイスを作成する | Microsoft Docs"
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
  - "フォーム, Windows エクスプローラー形式"
  - "SplitContainer コントロール [Windows フォーム], Explorer-style インターフェイス"
  - "Windows エクスプローラー, 作成 (Windows フォームを使用して)"
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : Windows フォームで Windows エクスプローラー スタイルのインターフェイスを作成する
Windows エクスプローラーは、そのユーザー インターフェイスがなじみ深いことから、多くのアプリケーションで採用されています。  
  
 基本的に Windows エクスプローラーとは、<xref:System.Windows.Forms.TreeView> コントロールと <xref:System.Windows.Forms.ListView> コントロールが独立したパネルに配置されたものです。  これらのパネルのサイズは、分割線で変更できます。  このようなコントロールの配置は、情報の表示と参照には非常に有効です。  
  
 次の手順では、Windows エクスプローラーに似た形式でコントロールを配置する方法を示します。  この手順では、Windows エクスプローラー アプリケーションのファイル参照機能を追加する方法は示しません。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### Windows エクスプローラー スタイルの Windows フォームを作成するには  
  
1.  新しい Windows アプリケーション プロジェクトを作成します。  詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
2.  **\[ツールボックス\]** で次の操作を行います。  
  
    1.  <xref:System.Windows.Forms.SplitContainer> コントロールをフォームにドラッグします。  
  
    2.  <xref:System.Windows.Forms.TreeView> コントロールを **\[SplitterPanel1\]** \(**\[Panel1\]** とマークされた <xref:System.Windows.Forms.SplitContainer> コントロールのパネル\) にドラッグします。  
  
    3.  <xref:System.Windows.Forms.ListView> コントロールを **\[SplitterPanel2\]** \(**\[panel2\]** とマークされた <xref:System.Windows.Forms.SplitContainer> コントロールのパネル\) にドラッグします。  
  
3.  Ctrl キーを押しながら、これら 3 つのコントロールすべてを順番にクリックして選択します。  <xref:System.Windows.Forms.SplitContainer> コントロールを選択するときは、パネルではなく、分割バーをクリックします。  
  
    > [!NOTE]
    >  **\[編集\]** メニューの **\[すべて選択\]** は使用しないでください。  このコマンドを使用すると、次の手順で必要なプロパティが **プロパティ** ウィンドウに表示されません。  
  
4.  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.Forms.SplitContainer.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle> に設定します。  
  
5.  F5 キーを押してアプリケーションを実行します。  
  
     フォームには、Windows エクスプローラーで使用されるような 2 つの部分に分かれたユーザー インターフェイスが表示されます。  
  
    > [!NOTE]
    >  分割線をドラッグすると、パネルのサイズが変更されます。  
  
## 参照  
 <xref:System.Windows.Forms.SplitContainer>   
 [方法 : Windows フォームでマルチペイン ユーザー インターフェイスを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)   
 [方法 : 分割ウィンドウでのサイズ変更および位置指定動作を定義する](../../../../docs/framework/winforms/controls/how-to-define-resize-and-positioning-behavior-in-a-split-window.md)   
 [方法 : ウィンドウを水平方向に分割する](../../../../docs/framework/winforms/controls/how-to-split-a-window-horizontally.md)   
 [SplitContainer コントロール](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)