---
title: "方法 : デザイナーを使用して Windows フォームでマルチペイン ユーザー インターフェイスを作成する | Microsoft Docs"
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
  - "マルチペイン ユーザー インターフェイス"
  - "SplitContainer コントロール [Windows フォーム], 使用 (デザイナーを)"
  - "ユーザー インターフェイス, マルチペイン"
ms.assetid: c3f9294d-a26c-4198-9242-f237f55f7573
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : デザイナーを使用して Windows フォームでマルチペイン ユーザー インターフェイスを作成する
次の手順では、Microsoft Outlook で使用されているユーザー インターフェイスに似た**フォルダー**一覧、**メッセージ** ペイン、および**プレビュー** ペインを備えたマルチペイン ユーザー インターフェイスを作成します。  これは、主にコントロールをフォームにドッキングして作成します。  
  
 コントロールをドッキングするときは、どちらの親コンテナーの端にコントロールを固定するかを決定します。  <xref:System.Windows.Forms.SplitContainer.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle> に設定した場合、コントロールの右端が親コントロールの右端にドッキングされます。  さらに、コントロールがドッキングされた端は、そのコンテナー コントロールに合うようにサイズ変更されます。  <xref:System.Windows.Forms.SplitContainer.Dock%2A> プロパティの機能の詳細については、「[方法 : Windows フォーム上のコントロールをドッキングする](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)」を参照してください。  
  
 この手順は、機能を追加してアプリケーションを Microsoft Outlook のようにするのではなく、フォーム上に <xref:System.Windows.Forms.SplitContainer> などのコントロールを配置します。  
  
 このユーザー インターフェイスを作成するには、左側のパネルに <xref:System.Windows.Forms.TreeView> コントロールを含む <xref:System.Windows.Forms.SplitContainer> コントロール内に、すべてのコントロールを配置します。  <xref:System.Windows.Forms.SplitContainer> コントロールの右側のパネルには、第 2 の <xref:System.Windows.Forms.SplitContainer> コントロールが含まれます。第 2 のコントロールでは、上部に <xref:System.Windows.Forms.ListView> コントロール、その下部に <xref:System.Windows.Forms.RichTextBox> コントロールが配置されます。  これらの <xref:System.Windows.Forms.SplitContainer> コントロールを使用すると、フォーム上の他のコントロールを個別にサイズ変更できます。  この手順に示される手法を応用して、独自のカスタム ユーザー インターフェイスを作成できます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### デザイン時に Outlook スタイルのユーザー インターフェイスを作成するには  
  
1.  新しい Windows アプリケーション プロジェクトを作成します。  詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
2.  **\[ツールボックス\]** から <xref:System.Windows.Forms.SplitContainer> コントロールをフォームにドラッグします。  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.Forms.SplitContainer.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle> に設定します。  
  
3.  **\[ツールボックス\]** から <xref:System.Windows.Forms.TreeView> コントロールを <xref:System.Windows.Forms.SplitContainer> コントロールの左側のパネルにドラッグします。  **\[プロパティ\]** ウィンドウで <xref:System.Windows.Forms.SplitContainer.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle> に設定します。これを行うには、値エディター \(下向きの矢印をクリックすると表示されるエディター\) で左側のパネルをクリックします。  
  
4.  **\[ツールボックス\]** から別の <xref:System.Windows.Forms.SplitContainer> コントロールをドラッグします。このコントロールは、既にフォームに追加している <xref:System.Windows.Forms.SplitContainer> コントロールの右側のパネルに配置します。  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.Forms.SplitContainer.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle> に、<xref:System.Windows.Forms.SplitContainer.Orientation%2A> プロパティを <xref:System.Windows.Forms.Orientation> に設定します。  
  
5.  **\[ツールボックス\]** から <xref:System.Windows.Forms.ListView> コントロールを、フォームに追加した第 2 の <xref:System.Windows.Forms.SplitContainer> コントロールの上部パネルにドラッグします。  <xref:System.Windows.Forms.ListView> コントロールの <xref:System.Windows.Forms.SplitContainer.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle> に設定します。  
  
6.  **\[ツールボックス\]** から <xref:System.Windows.Forms.RichTextBox> コントロールを、第 2 の <xref:System.Windows.Forms.SplitContainer> コントロールの下部パネルにドラッグします。  <xref:System.Windows.Forms.RichTextBox> コントロールの <xref:System.Windows.Forms.SplitContainer.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle> に設定します。  
  
     この時点で F5 キーを押してアプリケーションを実行すると、フォームには、Microsoft Outlook で使用されるような 3 つの部分に分かれたユーザー インターフェイスが表示されます。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.SplitContainer> コントロール内のいずれかの境界線上にマウス ポインターを移動すると、内部寸法のサイズを変更できます。  
  
     アプリケーション開発のこの時点で、非常に洗練されたユーザー インターフェイスが作成されました。  次の手順では、<xref:System.Windows.Forms.TreeView> コントロールと <xref:System.Windows.Forms.ListView> コントロールをデータ ソースに連結して、アプリケーション自体のプログラミングに進みます。  コントロールのデータへの連結の詳細については、「[データ連結と Windows フォーム](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.SplitContainer>   
 [SplitContainer コントロール](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)