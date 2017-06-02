---
title: "方法 : TableLayoutPanel コントロールの行と列を拡大する | Microsoft Docs"
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
  - "net.ComponentModel.StyleCollectionEditor.TLP.SpanRowsColumns"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "セル, マージ"
  - "列 [Windows フォーム], 拡張"
  - "マージ (セルを)"
  - "行 [Windows フォーム], 拡張"
  - "TableLayoutPanel コントロール [Windows フォーム], 拡張 (行と列を)"
ms.assetid: a8a2fdd3-a848-48b0-a4cd-4e85ebded87e
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : TableLayoutPanel コントロールの行と列を拡大する
<xref:System.Windows.Forms.TableLayoutPanel> コントロール内のコントロールは隣接する行と列に拡大できます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### 列と行を拡大するには  
  
1.  **ツールボックス**からフォームに、<xref:System.Windows.Forms.TableLayoutPanel> コントロールをドラッグします。  
  
2.  **ツールボックス**の <xref:System.Windows.Forms.Button> コントロールを <xref:System.Windows.Forms.TableLayoutPanel> コントロールの左上のセルにドラッグします。  
  
3.  <xref:System.Windows.Forms.Button> コントロールの **ColumnSpan** プロパティを 2 に設定します。  <xref:System.Windows.Forms.Button> コントロールは 1 番目と 2 番目の列にまたがります。  
  
4.  <xref:System.Windows.Forms.Button> コントロールの **RowSpan** プロパティを 2 に設定します。  <xref:System.Windows.Forms.Button> コントロールは 1 番目と 2 番目の行にまたがります。  
  
5.  <xref:System.Windows.Forms.Button> コントロールの **ColumnSpan** プロパティを 1 に設定します。  <xref:System.Windows.Forms.Button> コントロールは最初の列に移動し、1 番目と 2 番目の行にまたがります。  
  
## 参照  
 [TableLayoutPanel コントロール](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)