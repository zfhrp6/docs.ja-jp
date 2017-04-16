---
title: "ProgressBar コントロールの概要 (Windows フォーム) | Microsoft Docs"
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
  - "ProgressBar"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "プログレス コントロール, プログレス コントロールの概要"
  - "ProgressBar コントロール [Windows フォーム], ProgressBar コントロールの概要"
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# ProgressBar コントロールの概要 (Windows フォーム)
> [!IMPORTANT]
>  <xref:System.Windows.Forms.ToolStripProgressBar> コントロールは、<xref:System.Windows.Forms.ProgressBar> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.ProgressBar> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  
  
 Windows フォームの <xref:System.Windows.Forms.ProgressBar> コントロールは、水平のバーに複数の四角形を表示することで、処理の進行状況を表します。  処理が完了したときには、バーが四角形で埋められます。  プログレス バーは、通常、処理が完了するまでの待機時間をユーザーに示すために使用します。たとえば、大きなファイルの読み込み時に使用します。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ProgressBar> コントロールは、フォーム上で水平方向にのみ配置できます。  
  
## 主要なプロパティおよびメソッド  
 <xref:System.Windows.Forms.ProgressBar> コントロールの主要なプロパティは、<xref:System.Windows.Forms.ProgressBar.Value%2A>、<xref:System.Windows.Forms.ProgressBar.Minimum%2A>、および <xref:System.Windows.Forms.ProgressBar.Maximum%2A> です。  <xref:System.Windows.Forms.ProgressBar.Minimum%2A> プロパティおよび <xref:System.Windows.Forms.ProgressBar.Maximum%2A> プロパティは、プログレス バーに表示できる最大値と最小値を設定するために使用します。  <xref:System.Windows.Forms.ProgressBar.Value%2A> プロパティは、操作が進行して完了した割合を表します。  コントロールに表示されるバーはブロックを並べて構成されるため、<xref:System.Windows.Forms.ProgressBar> コントロールによって示される値は、<xref:System.Windows.Forms.ProgressBar.Value%2A> プロパティの現在の値の近似値にすぎません。  <xref:System.Windows.Forms.ProgressBar> コントロールのサイズに基づいて、<xref:System.Windows.Forms.ProgressBar.Value%2A> プロパティで次のブロックがいつ表示されるかが決定されます。  
  
 現在の進行状況の値を更新する最も一般的な方法は、<xref:System.Windows.Forms.ProgressBar.Value%2A> プロパティを設定するコードを記述することです。  たとえば、大きいファイルの読み込みを行うときは、最大値として、ファイルの大きさを KB 単位で設定します。  たとえば、<xref:System.Windows.Forms.ProgressBar.Maximum%2A> プロパティが 100 に設定され、<xref:System.Windows.Forms.ProgressBar.Minimum%2A> プロパティが 10 に設定され、さらに <xref:System.Windows.Forms.ProgressBar.Value%2A> プロパティが 50 に設定されている場合は、5 つの四角形が表示されます。  これは、表示できる数の半分です。  
  
 ただし、<xref:System.Windows.Forms.ProgressBar.Value%2A> プロパティを直接設定する以外にも、<xref:System.Windows.Forms.ProgressBar> コントロールによって表示される値を変更する方法があります。  <xref:System.Windows.Forms.ProgressBar.Step%2A> プロパティを使用して、<xref:System.Windows.Forms.ProgressBar.Value%2A> プロパティをインクリメントする幅を指定できます。  次に、<xref:System.Windows.Forms.ProgressBar.PerformStep%2A> メソッドを呼び出して値をインクリメントします。  インクリメント幅を変更する場合は、<xref:System.Windows.Forms.ProgressBar.Increment%2A> メソッドを使用して、<xref:System.Windows.Forms.ProgressBar.Value%2A> プロパティをインクリメントする値を指定します。  
  
 現在の処理状況をグラフィカルに表示するもう 1 つのコントロールは、<xref:System.Windows.Forms.StatusBar> コントロールです。  
  
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> コントロールと <xref:System.Windows.Forms.ToolStripStatusLabel> コントロールは、<xref:System.Windows.Forms.StatusBar> コントロールおよび <xref:System.Windows.Forms.StatusBarPanel> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.StatusBar> コントロールおよび <xref:System.Windows.Forms.StatusBarPanel> コントロールは、下位互換性を保つ目的および将来使用する目的で、必要に応じて保持できます。  
  
## 参照  
 <xref:System.Windows.Forms.ProgressBar>   
 [ProgressBar コントロール](../../../../docs/framework/winforms/controls/progressbar-control-windows-forms.md)