---
title: "方法 : TableLayoutPanel コントロール内でコントロールを配置して伸縮する | Microsoft Docs"
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
  - "net.ComponentModel.StyleCollectionEditor.TLP.AlignStretchCtrl"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "コントロール [Windows フォーム], エイリアスの使用"
  - "コントロール [Windows フォーム], 拡大"
  - "TableLayoutPanel コントロール [Windows フォーム], 拡大 (コントロールを)"
ms.assetid: 7dc1a157-6fee-4995-8ebc-b65bdc0909a8
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : TableLayoutPanel コントロール内でコントロールを配置して伸縮する
<xref:System.Windows.Forms.Control.Anchor%2A> プロパティと <xref:System.Windows.Forms.Control.Dock%2A> プロパティを使用すると、<xref:System.Windows.Forms.TableLayoutPanel> 内でコントロールを配置して伸縮できます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### コントロールを配置して伸縮するには  
  
1.  **ツールボックス**からフォームに、<xref:System.Windows.Forms.TableLayoutPanel> コントロールをドラッグします。  
  
2.  **ツールボックス**の <xref:System.Windows.Forms.Button> コントロールを <xref:System.Windows.Forms.TableLayoutPanel> コントロールの左上のセルにドラッグします。  <xref:System.Windows.Forms.Button> コントロールはセルの中央に配置されます。  
  
3.  <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を `Left,Right` に設定します。  <xref:System.Windows.Forms.Button> コントロールがセルの幅に合わせて伸縮します。  
  
4.  <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を `Top,Bottom` に設定します。  <xref:System.Windows.Forms.Button> コントロールがセルの高さに合わせて伸縮します。  
  
5.  <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Dock%2A> プロパティの値を <xref:System.Windows.Forms.DockStyle> に設定します。  <xref:System.Windows.Forms.Button> コントロールがセル全体に拡張します。  
  
6.  <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Dock%2A> プロパティの値を <xref:System.Windows.Forms.DockStyle> に設定します。  <xref:System.Windows.Forms.Button> コントロールが元のサイズに戻り、セルの左上隅に移動します。  **Windows フォーム デザイナー**で <xref:System.Windows.Forms.Control.Anchor%2A> プロパティが `Top, Left` に設定されているからです。  
  
7.  <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を `Bottom,Right` に設定します。  <xref:System.Windows.Forms.Button> コントロールがセルの右下隅に移動します。  
  
8.  <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を <xref:System.Windows.Forms.AnchorStyles> に設定します。  <xref:System.Windows.Forms.Button> コントロールがセルの中央に移動します。  
  
## 参照  
 [TableLayoutPanel コントロール](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)