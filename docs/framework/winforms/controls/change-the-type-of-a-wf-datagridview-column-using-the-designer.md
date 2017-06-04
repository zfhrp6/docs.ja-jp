---
title: "方法 : デザイナーを使用して Windows フォーム DataGridView 列の種類を変更する | Microsoft Docs"
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
  - "列 [Windows フォーム], 種類"
  - "データ [Windows フォーム], 表示"
  - "DataGridView コントロール [Windows フォーム], 変更 (列型を)"
  - "Windows フォーム, 列"
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : デザイナーを使用して Windows フォーム DataGridView 列の種類を変更する
場合によっては、既に Windows フォーム <xref:System.Windows.Forms.DataGridView> コントロールに追加されている列の種類を変更する必要があります。  たとえば、コントロールをデータ ソースにバインドしたときに、自動的に生成される一部の列の種類を変更できます。  これは、表示するテーブルに、関連テーブル内の行への外部キーを含む列がある場合に便利です。  この場合、これらの外部キーを表示するテキスト ボックス列を、関連テーブルのより意味のある値を表示するコンボ ボックス列と置き換える必要があります。  
  
 次の手順では、<xref:System.Windows.Forms.DataGridView> コントロールを含むフォームを持つ **Windows アプリケーション** プロジェクトが必要です。  このプロジェクトの設定の詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」および「[方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### デザイナーを使用して列の種類を変更するには  
  
1.  <xref:System.Windows.Forms.DataGridView> コントロールの右上隅にあるスマート タグ グリフ \(![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\) をクリックして、**\[列の編集\]** を選択します。  
  
2.  **\[選択された列\]** ボックスの一覧で列を選択します。  
  
3.  **\[列のプロパティ\]** グリッド内で、`ColumnType` プロパティを新しい列の種類に設定します。  
  
    > [!NOTE]
    >  `ColumnType` プロパティは、デザイン時のみのプロパティで、列の種類を表すクラスを示します。  これは列クラス内に定義される実際のプロパティではありません。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewColumn>   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)   
 [方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)