---
title: "方法 : TabControl を使用して側面に位置を合わせて表示する | Microsoft Docs"
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
  - "タブ ページ, 表示 (側面に位置を合わせたタブを)"
  - "TabControl コントロール [Windows フォーム], 表示 (側面に位置を合わせたタブを)"
  - "タブ, 表示 (側面に位置を合わせたタブを)"
ms.assetid: 110d5abd-3ae3-4ded-95bf-778aaac798a0
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : TabControl を使用して側面に位置を合わせて表示する
<xref:System.Windows.Forms.TabControl> の <xref:System.Windows.Forms.TabControl.Alignment%2A> プロパティは、水平方向 \(コントロールの上部または下部\) ではなく、垂直方向 \(コントロールの左端または右端\) でのタブの表示をサポートします。  <xref:System.Windows.Forms.TabPage> オブジェクトの <xref:System.Windows.Forms.TabPage.Text%2A> プロパティは、視覚スタイルを有効にしたときにタブが表示されないため、既定では、この垂直方向の表示はユーザーの操作性が低下します。  また、タブ内のテキストの方向を制御する直接的な方法がありません。  この操作性を向上させるために、<xref:System.Windows.Forms.TabControl> でオーナー描画を使用できます。  
  
 次の手順では、「オーナー描画」機能を使用して、タブのテキストが左から右に実行されているときに、右揃えのタブを表示する方法を示します。  
  
### 右揃えのタブを表示するには  
  
1.  <xref:System.Windows.Forms.TabControl> をフォームに追加します。  
  
2.  <xref:System.Windows.Forms.TabControl.Alignment%2A> プロパティを <xref:System.Windows.Forms.TabAlignment> に設定します。  
  
3.  <xref:System.Windows.Forms.TabControl.SizeMode%2A> プロパティを <xref:System.Windows.Forms.TabSizeMode> に設定して、すべてのタブが同じ幅になるようにします。  
  
4.  タブの <xref:System.Windows.Forms.TabControl.ItemSize%2A> プロパティを任意の固定サイズに設定します。  <xref:System.Windows.Forms.TabControl.ItemSize%2A> プロパティは、タブが右揃えでも、最上部にあるように機能することに注意してください。  その結果、タブを広くするには <xref:System.Drawing.Size.Height%2A> プロパティを変更する必要があり、高くするには <xref:System.Drawing.Size.Width%2A> プロパティを変更する必要があります。  
  
     次のコード例で最適な結果を得るには、タブの <xref:System.Drawing.Size.Width%2A> を 25 に設定し、<xref:System.Drawing.Size.Height%2A> を 100 に設定します。  
  
5.  <xref:System.Windows.Forms.TabControl.DrawMode%2A> プロパティを <xref:System.Windows.Forms.TabDrawMode> に設定します。  
  
6.  テキストを左から右に表示する <xref:System.Windows.Forms.TabControl> の <xref:System.Windows.Forms.TabControl.DrawItem> イベントのハンドラーを定義します。  
  
     [!code-csharp[TabControl.RightAlignedTabs#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/TabControl.RightAlignedTabs/CS/Form1.cs#1)]
     [!code-vb[TabControl.RightAlignedTabs#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/TabControl.RightAlignedTabs/VB/Form1.vb#1)]  
  
## 参照  
 [TabControl コントロール](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)