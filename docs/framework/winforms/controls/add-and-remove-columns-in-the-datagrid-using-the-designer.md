---
title: "方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列を追加および削除する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.DataGridViewAddColumnDialog"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "DataGridView コントロール [Windows フォーム], 追加 (列を)"
  - "DataGridView コントロール [Windows フォーム], 削除 (列を)"
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列を追加および削除する
Windows フォーム <xref:System.Windows.Forms.DataGridView> コントロールには、データを表示するための列を含める必要があります。  コントロールに手動でデータを設定する場合は、手動で列を追加する必要があります。  別の方法として、コントロールをデータ ソースにバインドすることもできます。この場合、自動的に列が生成されデータが読み込まれます。  表示する列数を超える列がデータ ソースに含まれるときは、不要な列を削除できます。  
  
 次の手順では、<xref:System.Windows.Forms.DataGridView> コントロールを含むフォームを持つ **Windows アプリケーション** プロジェクトが必要です。  このプロジェクトの設定の詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」および「[方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### デザイナーを使用して列を追加するには  
  
1.  <xref:System.Windows.Forms.DataGridView> コントロールの右上隅にあるスマート タグ グリフ \(![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\) をクリックして、**\[列の追加\]** を選択します。  
  
2.  **\[列の追加\]** ダイアログ ボックスで、**\[データバインド列\]** を選択し、データ ソースの列を選択します。または、**\[非バインド列\]** を選択し、提供されたフィールドを使用して列を定義します。  
  
3.  **\[追加\]** をクリックして列を追加します。既存の列がコントロールの表示領域いっぱいに表示されていない場合は、追加した列がデザイナーに表示されます。  
  
    > [!NOTE]
    >  列のプロパティは、コントロールのスマート タグからアクセスできる **\[列の編集\]** ダイアログ ボックスで変更できます。  
  
### デザイナーを使用して列を削除するには  
  
1.  コントロールのスマート タグの **\[列の編集\]** をクリックします。  
  
2.  **\[選択された列\]** ボックスの一覧で列を選択します。  
  
3.  **\[削除\]** をクリックして列を削除します。削除した列がデザイナーに表示されなくなります。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)   
 [方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)