---
title: "TrackBar コントロールの概要 (Windows フォーム) | Microsoft Docs"
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
  - "TrackBar"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "スライダー コントロール, スライダー コントロールの概要"
  - "スライダー, スライダーの概要"
  - "TrackBar コントロール [Windows フォーム], TrackBar コントロールの概要"
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# TrackBar コントロールの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.TrackBar> コントロールは、"スライダー" コントロールとも呼ばれ、大量の情報内を移動する場合や、数値設定を視覚的に調整する場合などに使用します。  <xref:System.Windows.Forms.TrackBar> コントロールは、つまみ \(スライダー\) と軸目盛りという 2 つの部分で構成されます。  つまみは調整できます。  つまみの位置は <xref:System.Windows.Forms.TrackBar.Value%2A> プロパティに対応しています。  軸目盛りは、一定の間隔で区切られた視覚的なインジケーターです。  トラック バーは、指定した単位で移動し、水平または垂直に調整できます。  たとえば、トラック バーを使用して、システムのカーソル点滅速度やマウス速度を制御できます。  
  
## 主要なプロパティ  
 <xref:System.Windows.Forms.TrackBar> コントロールの主要なプロパティは、<xref:System.Windows.Forms.TrackBar.Value%2A>、<xref:System.Windows.Forms.TrackBar.TickFrequency%2A>、<xref:System.Windows.Forms.TrackBar.Minimum%2A>、および <xref:System.Windows.Forms.TrackBar.Maximum%2A> です。  <xref:System.Windows.Forms.TrackBar.TickFrequency%2A> は、軸目盛りの間隔です。  <xref:System.Windows.Forms.TrackBar.Minimum%2A> および <xref:System.Windows.Forms.TrackBar.Maximum%2A> は、トラック バーに表示できる最小値および最大値です。  
  
 その他に、<xref:System.Windows.Forms.TrackBar.SmallChange%2A> と <xref:System.Windows.Forms.TrackBar.LargeChange%2A> という 2 つの重要なプロパティがあります。  <xref:System.Windows.Forms.TrackBar.SmallChange%2A> プロパティの値は、左右の方向キーを押したときにつまみが移動する目盛りの数です。  <xref:System.Windows.Forms.TrackBar.LargeChange%2A> プロパティの値は、PageUp キーまたは PageDown キーを押したとき、またはトラック バー上でつまみの左右をマウス クリックしたときに、つまみが移動する目盛りの数です。  
  
## 参照  
 <xref:System.Windows.Forms.TrackBar>   
 [TrackBar コントロール](../../../../docs/framework/winforms/controls/trackbar-control-windows-forms.md)