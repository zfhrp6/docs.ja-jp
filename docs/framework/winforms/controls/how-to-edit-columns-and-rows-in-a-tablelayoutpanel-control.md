---
title: "方法 : TableLayoutPanel コントロールの列と行を編集する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "net.ComponentModel.StyleCollectionEditor"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "列 [Windows フォーム], 編集"
  - "行 [Windows フォーム], 編集"
  - "TableLayoutPanel コントロール [Windows フォーム], 編集"
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : TableLayoutPanel コントロールの列と行を編集する
<xref:System.Windows.Forms.TableLayoutPanel> コントロールのコレクション エディター \(**\[列と行のスタイル\]** ダイアログ ボックス\) を使用して、コントロールの行と列を編集できます。  
  
> [!NOTE]
>  コントロールが複数の行または列にわたるようにする場合は、コントロールの `RowSpan` プロパティおよび `ColumnSpan` プロパティを設定します。  詳細については、「[チュートリアル : TableLayoutPanel を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)」を参照してください。  
>   
>  コントロールをセル内に配置したり、コントロールをセル内で拡大したりする場合は、コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティを使用します。  詳細については、「[チュートリアル : TableLayoutPanel を使用した Windows フォーム上のコントロールの配置](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)」を参照してください。  
>   
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### 行と列を編集するには  
  
1.  **ツールボックス**からフォームに、<xref:System.Windows.Forms.TableLayoutPanel> コントロールをドラッグします。  
  
2.  <xref:System.Windows.Forms.TableLayoutPanel> コントロールのスマート タグ グリフ \(![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\) をクリックし、**\[行および列の編集\]** をクリックして、**\[列と行のスタイル\]** ダイアログ ボックスを開きます。  <xref:System.Windows.Forms.TableLayoutPanel> コントロールを右クリックして、ショートカット メニューの **\[行および列の編集\]** をクリックすることもできます。  
  
3.  列を追加または削除するには、**\[型\]** ボックスの **\[列\]** をクリックします。  
  
4.  行を追加または削除するには、**\[型\]** ボックスの **\[行\]** をクリックします。  
  
5.  **\[追加\]** をクリックすると、行または列が **\[メンバー\]** 一覧の末尾に追加されます。  
  
6.  **\[挿入\]** をクリックすると、一覧で現在選択されている項目の前に行または列が追加されます。  
  
7.  行または列を追加する場合は、新しい行または列の **\[サイズの型\]** を選択します。  詳細については、「<xref:System.Windows.Forms.SizeType>」を参照してください。  
  
8.  行または列を削除するには、**\[削除\]** をクリックします。**\[メンバー\]** 一覧で現在選択されている項目が削除されます。  
  
## 参照  
 <xref:System.Windows.Forms.SizeType>   
 [TableLayoutPanel コントロール](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)