---
title: "TableLayoutPanel コントロールにおける AutoSize 動作 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "サイズの自動調整"
  - "AutoSize プロパティ, TableLayoutPanel コントロール"
  - "AutoSizeMode プロパティ"
  - "コントロール [Windows フォーム], サイズ変更"
  - "レイアウト [Windows フォーム], AutoSize"
  - "ローカライズ (フォームを)"
  - "サイズ変更, 自動"
  - "TableLayoutPanel コントロール [Windows フォーム], AutoSize の動作"
ms.assetid: 9233e0c3-2fa6-405e-8701-959479b1250e
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# TableLayoutPanel コントロールにおける AutoSize 動作
## 異なる AutoSize 動作  
 <xref:System.Windows.Forms.TableLayoutPanel> コントロールは、次の方法で自動サイズ変更動作をサポートします。  
  
-   <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティを使用する。  
  
-   <xref:System.Windows.Forms.TableLayoutPanel> コントロールの列スタイルと行スタイルで <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> プロパティを使用する。  
  
### AutoSize プロパティと列および行スタイル  
 <xref:System.Windows.Forms.Control.AutoSize%2A> プロパティと <xref:System.Windows.Forms.TableLayoutPanel> コントロールの列\/行スタイルとの対応について次の表に示します。  
  
|AutoSize の設定|スタイルに関する対応|  
|------------------|----------------|  
|`false`|<xref:System.Windows.Forms.TableLayoutPanel> コントロールは左から右に処理を実行し、次の順序で列または行の領域を割り当てます。<br /><br /> 1.  <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> プロパティが <xref:System.Windows.Forms.SizeType> に設定されている場合は、<xref:System.Windows.Forms.ColumnStyle.Width%2A> または <xref:System.Windows.Forms.RowStyle.Height%2A> で指定されているピクセル数を割り当てます。<br />2.  <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> プロパティが <xref:System.Windows.Forms.SizeType> に設定されている場合は、子コントロールの <xref:System.Windows.Forms.Control.GetPreferredSize%2A> メソッドが返すピクセル数を割り当てます。<br />3.  すべての <xref:System.Windows.Forms.SizeType> 列\/行と <xref:System.Windows.Forms.SizeType> 列\/行の領域を割り当てると、<xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> が <xref:System.Windows.Forms.SizeType> に設定されている列または行を使用して残りの空き領域を比例的に割り当てます。|  
|`true`|<xref:System.Windows.Forms.SizeType> 列\/行が自動サイズ変更アスペクトを取得することを除いて、上記の対応と同様です。<br /><br /> <xref:System.Windows.Forms.TableLayoutPanel> コントロールは、<xref:System.Windows.Forms.SizeType> スタイルが設定された列または行によって内容がクリップされないように、列または行を拡張して十分な空き領域を作成します。  <xref:System.Windows.Forms.TableLayoutPanel> コントロールは、<xref:System.Windows.Forms.ColumnStyle.Width%2A> プロパティまたは <xref:System.Windows.Forms.RowStyle.Height%2A> プロパティに従って、新しい領域を比例的に割り当てます。|  
  
## 参照  
 <xref:System.Windows.Forms.TableLayoutPanel>   
 [TableLayoutPanel コントロールの概要](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-overview.md)