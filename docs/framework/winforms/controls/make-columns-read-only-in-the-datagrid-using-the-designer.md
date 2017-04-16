---
title: "方法 : デザイナーを使用して Windows フォームの DataGridView コントロールで列を読み取り専用にする | Microsoft Docs"
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
  - "列 [Windows フォーム], 読み取り専用"
  - "データ [Windows フォーム], 表示"
  - "DataGridView コントロール [Windows フォーム], 読み取り専用列"
  - "Windows フォーム, 列"
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 方法 : デザイナーを使用して Windows フォームの DataGridView コントロールで列を読み取り専用にする
既定では、ユーザーは Windows フォーム <xref:System.Windows.Forms.DataGridView> コントロールに表示されるテキストと数値データを変更できます。  表示するデータを変更できないようにする場合は、データを含む列を読み取り専用にする必要があります。  コントロールを完全に読み取り専用にする方法の詳細については、「[方法 : デザイナーを使用して Windows フォーム DataGridView コントロールで行が追加および削除されないようにする](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)」を参照してください。  
  
 次の手順では、<xref:System.Windows.Forms.DataGridView> コントロールを含むフォームを持つ **Windows アプリケーション** プロジェクトが必要です。  このプロジェクトの設定の詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」および「[方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### デザイナーを使用して列を読み取り専用にするには  
  
1.  <xref:System.Windows.Forms.DataGridView> コントロールの右上隅にあるスマート タグ グリフ \(![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\) をクリックして、**\[列の編集\]** を選択します。  
  
2.  **\[選択された列\]** ボックスの一覧で列を選択します。  
  
3.  **\[列のプロパティ\]** グリッドで、<xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> プロパティを `true` に設定します。  
  
    > [!NOTE]
    >  **\[列の追加\]** ダイアログ ボックスの **\[読み取り専用\]** チェック ボックスをオンにすることによって、列の追加時に列を読み取り専用にすることもできます。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=fullName>   
 [方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列を追加および削除する](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)   
 [方法 : デザイナーを使用して Windows フォーム DataGridView コントロールで行が追加および削除されないようにする](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)   
 [方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)