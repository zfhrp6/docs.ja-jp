---
title: "方法 : デザイナーを使用して Windows フォーム DataGridView コントロールに交互の行のスタイルを設定する | Microsoft Docs"
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
  - "データ [Windows フォーム], 表示"
  - "DataGridView コントロール [Windows フォーム], 行スタイル (交互の行)"
  - "帳簿のような形式"
  - "行, 交互の"
  - "Windows フォーム, 行"
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : デザイナーを使用して Windows フォーム DataGridView コントロールに交互の行のスタイルを設定する
多くの場合、表形式データは、交互の行が異なる背景色を持つ帳簿のような形式で示されます。  この形式では、行とセルの位置関係を見極めやすく、列数が多く幅の広い表では特に便利です。  
  
 <xref:System.Windows.Forms.DataGridView> コントロールを使用すると、交互の行に対して完全なスタイル情報を指定できます。  このコントロールでは、背景色だけでなく前景色やフォントなどのスタイル特性を使用して、交互の行を区別化できます。  詳細については、「[Windows フォーム DataGridView コントロールでのセルのスタイル](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
 次の手順では、<xref:System.Windows.Forms.DataGridView> コントロールを含むフォームを持つ **Windows アプリケーション** プロジェクトが必要です。  このプロジェクトの設定の詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」および「[方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### 交互の行のスタイルの定義  
  
1.  デザイナーで <xref:System.Windows.Forms.DataGridView> コントロールを選択します。  
  
2.  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> プロパティの横にある省略記号ボタン \(![VisualStudioEllipsesButton スクリーンショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) をクリックします。  
  
3.  **\[CellStyle ビルダー\]** ダイアログ ボックスで、プロパティを設定してスタイルを定義し、**プレビュー** ペインを使用して選択内容を確定します。  指定するスタイルは、コントロールに表示される 2 番目の行以降、1 行おきに適用されます。  
  
4.  残りの行のスタイルを定義するには、<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> プロパティを使用して手順 2. と手順 3. を繰り返します。  
  
    > [!NOTE]
    >  セルは複数のプロパティから継承したスタイルを使用して表示されます。  スタイルの継承の詳細については、「[Windows フォーム DataGridView コントロールでのセルのスタイル](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 [Windows フォーム DataGridView コントロールでのセルのスタイル](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)   
 [Windows フォームの DataGridView コントロールの基本的な書式設定およびスタイル設定](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールでのデザイナーの使用](../../../../docs/framework/winforms/controls/using-the-designer-with-the-windows-forms-datagridview-control.md)   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)   
 [方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)