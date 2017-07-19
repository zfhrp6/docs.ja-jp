---
title: "方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列の順序を変更する | Microsoft Docs"
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
  - "列 [Windows フォーム], 順序"
  - "データ [Windows フォーム], 表示"
  - "DataGridView コントロール [Windows フォーム], 列の順序"
  - "Windows フォーム, 列"
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列の順序を変更する
Windows フォーム <xref:System.Windows.Forms.DataGridView> コントロールをデータ ソースにバインドすると、自動的に生成される列の表示順序がデータ ソースによって指定されます。  この順序が好ましくない場合は、デザイナーを使用して列の順序を変更できます。  また、非バインド列をコントロールに追加して、それらの表示順序を変更することもできます。  列の順序をプログラムで変更する方法については、「[方法 : Windows フォーム DataGridView コントロールの列の順序を変更する](../../../../docs/framework/winforms/controls/how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
 次の手順では、<xref:System.Windows.Forms.DataGridView> コントロールを含むフォームを持つ **Windows アプリケーション** プロジェクトが必要です。  このプロジェクトの設定の詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」および「[方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### デザイナーを使用して列の順序を変更するには  
  
1.  <xref:System.Windows.Forms.DataGridView> コントロールの右上隅にあるスマート タグ グリフ \(![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\) をクリックして、**\[列の編集\]** を選択します。  
  
2.  **\[選択された列\]** ボックスの一覧で列を選択します。  
  
3.  **\[選択された列\]** ボックスの右側にある上向きまたは下向きの矢印をクリックして、選択した列を目的の位置に移動します。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 [方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列を追加および削除する](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)   
 [方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)