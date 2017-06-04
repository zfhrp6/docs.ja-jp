---
title: "方法 : デザイナーを使って Windows フォーム ListView コントロールの &quot;並べて表示&quot; ビューを有効にする | Microsoft Docs"
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
  - "ListView コントロール [Windows フォーム], 並べて表示ビュー"
  - "並べて表示ビュー機能"
  - "タイリング, Windows フォーム, コントロール"
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : デザイナーを使って Windows フォーム ListView コントロールの &quot;並べて表示&quot; ビューを有効にする
<xref:System.Windows.Forms.ListView> コントロールの並べて表示ビュー機能を使用すると、グラフィカルな情報とテキスト情報をバランスよく表示できます。  並べて表示ビューの項目で表示されるテキスト情報は、詳細表示用に定義されている列情報と同じ情報です。  並べて表示ビューは、<xref:System.Windows.Forms.ListView> コントロールのグループ化機能または挿入マーク機能のいずれかと組み合わせて使用できます。  
  
 並べて表示ビューでは、サイズが 32 × 32 のアイコンと数行のテキストが以下のイメージのように使用されます。  
  
 ![ListView コントロール内のタイル ビュー](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")  
  
 並べて表示ビューのプロパティとメソッドを使用すると、各項目をどの列フィールドに表示するのかを指定でき、並べて表示ビュー ウィンドウ内の全項目のサイズと外観をまとめて制御できます。  また、並べて表示ビューでは、テキストの最初の行は常に項目の名前となり、変更できません。  
  
 次の手順では、<xref:System.Windows.Forms.ListView> コントロールが含まれているフォームを持つ **Windows アプリケーション** プロジェクトが必要です。  このプロジェクトの設定の詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」および「[方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)」を参照してください。  
  
> [!NOTE]
>  並べて表示ビューを [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] で使用できるのは、アプリケーションから <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=fullName> メソッドを呼び出した場合だけです。  旧バージョンのオペレーティング システムでは、タイル ビューに関するコードがすべて無効になり、<xref:System.Windows.Forms.ListView> コントロールは大きなアイコンのビューで表示されます。  詳細については、「<xref:System.Windows.Forms.ListView.View%2A?displayProperty=fullName>」を参照してください。  
>   
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### デザイナーで並べて表示ビューを設定するには  
  
1.  フォームで <xref:System.Windows.Forms.ListView> コントロールを選択します。  
  
2.  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.Forms.ListView.View%2A> プロパティをクリックし、**\[Tile\]** を選択します。  
  
## 参照  
 <xref:System.Windows.Forms.ListView.TileSize%2A>   
 [Windows XP Features and Windows Forms Controls](http://msdn.microsoft.com/ja-jp/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)   
 [ListView コントロールの概要](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)