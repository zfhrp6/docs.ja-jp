---
title: "方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列を非表示にする | Microsoft Docs"
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
  - "列 [Windows フォーム], 非表示"
  - "データ [Windows フォーム], 表示"
  - "DataGridView コントロール [Windows フォーム], 列の非表示"
  - "Windows フォーム, 列"
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列を非表示にする
Windows フォームの <xref:System.Windows.Forms.DataGridView> コントロールで使用できる列のうち、一部の列だけを表示する必要が生じる場合があります。  たとえば、従業員の給与の列を管理の資格情報を持つユーザーには表示して、他のユーザーには非表示にできます。  または、多くの列を含むデータ ソースにコントロールをバインドし、そのいくつかだけを表示することもできます。  この場合、通常、表示しない列は非表示にするのではなく削除します。  詳細については、「[方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列を追加および削除する](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)」を参照してください。  
  
 次の手順では、<xref:System.Windows.Forms.DataGridView> コントロールを含むフォームを持つ **Windows アプリケーション** プロジェクトが必要です。  このプロジェクトの設定の詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」および「[方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### デザイナーを使用して列を非表示にするには  
  
1.  <xref:System.Windows.Forms.DataGridView> コントロールの右上隅にあるスマート タグ グリフ \(![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\) をクリックして、**\[列の編集\]** を選択します。  
  
2.  **\[選択された列\]** ボックスの一覧で列を選択します。  
  
3.  **\[列のプロパティ\]** グリッドで、<xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> プロパティを `false` に設定します。  
  
    > [!NOTE]
    >  また、**\[列の追加\]** ダイアログ ボックスの **\[可視\]** ボックスをオフすることによって、列の追加時に列を非表示にすることもできます。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=fullName>   
 [方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列を追加および削除する](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)   
 [方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)