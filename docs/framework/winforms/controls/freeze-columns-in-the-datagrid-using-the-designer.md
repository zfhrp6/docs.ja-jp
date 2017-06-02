---
title: "方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列を固定する | Microsoft Docs"
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
  - "列 [Windows フォーム], 固定"
  - "データ [Windows フォーム], 表示"
  - "DataGridView コントロール [Windows フォーム], 列の固定"
  - "Windows フォーム, 列"
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列を固定する
Windows フォーム <xref:System.Windows.Forms.DataGridView> コントロールに表示されたデータを確認する場合、ユーザーは 1 つの列または複数の列を頻繁に参照しなければならないことがあります。  たとえば、多くの列を含む顧客情報の表を表示する場合、顧客名を常に表示したまま、その他の列は表示可能な領域外にスクロールできるようにすると便利です。  
  
 このようにするには、コントロール内で列を固定します。  列を固定すると、その左側の \(または右から左に記述される言語スクリプトでは右側の\) すべての列も同様に固定されます。  固定された列は所定の位置に表示されたままですが、その他の列はすべてスクロールできます。  列の順序変更を有効にしている場合、固定されている列は、固定されていない列とは異なるグループと見なされます。  ユーザーはグループ内で列を再配置できますが、異なるグループには列を移動できません。  
  
 次の手順では、<xref:System.Windows.Forms.DataGridView> コントロールを含むフォームを持つ **Windows アプリケーション** プロジェクトが必要です。  このプロジェクトの設定の詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」および「[方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### デザイナーを使用して列を固定するには  
  
1.  <xref:System.Windows.Forms.DataGridView> コントロールの右上隅にあるスマート タグ グリフ \(![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\) をクリックして、**\[列の編集\]** を選択します。  
  
2.  **\[選択された列\]** ボックスの一覧で列を選択します。  
  
3.  **\[列のプロパティ\]** グリッドで、<xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> プロパティを `true` に設定します。  
  
    > [!NOTE]
    >  また、**\[列の追加\]** ダイアログ ボックスの **\[固定\]** ボックスを選択することによって、列を追加する際に固定することもできます。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=fullName>   
 [方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列を追加および削除する](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)   
 [方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列の並べ替えを有効にする](../../../../docs/framework/winforms/controls/enable-column-reordering-in-the-datagrid-using-the-designer.md)   
 [How to: Display Right\-to\-Left Text in Windows Forms for Globalization](http://msdn.microsoft.com/ja-jp/f0663385-2354-4c65-8676-706422283b14)   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)   
 [方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)