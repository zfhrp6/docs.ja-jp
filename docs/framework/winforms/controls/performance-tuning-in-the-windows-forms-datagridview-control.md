---
title: "Windows フォーム DataGridView コントロールでのパフォーマンス チューニング | Microsoft Docs"
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
  - "DataGridView コントロール [Windows フォーム], パフォーマンス チューニング"
  - "パフォーマンス チューニング, データ グリッド"
  - "パフォーマンス, DataGridView コントロール"
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Windows フォーム DataGridView コントロールでのパフォーマンス チューニング
`DataGridView` コントロールで大量のデータを扱うときは、慎重に使用しないと、オーバーヘッドのために大量のメモリが消費されることがあります。  クライアントのメモリが限られている場合は、メモリ消費の多い機能を使わないようにすることで、このオーバーヘッドをある程度回避できます。  また、仮想モードを使用して一部または全部のデータ保守タスクとデータ取得タスクを自力で管理すると、メモリ使用状況をシナリオに合わせてカスタマイズできます。  
  
## このセクションの内容  
 [Windows フォーム DataGridView コントロールを拡張するための推奨される手順](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 大量のデータを扱うときに、無用なメモリ消費とパフォーマンス低下を避けるような方法で `DataGridView` コントロールを使用するための詳細を説明します。  
  
 [Windows フォーム DataGridView コントロールでの仮想モード](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 仮想モードを使用して標準のデータ バインディング機構を補完する \(または置き換える\) 方法について説明します。  
  
 [チュートリアル : Windows フォーム DataGridView コントロールでの仮想モードの実装](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 いくつかの仮想モード イベントのハンドラーを実装する方法について説明します。  また、ユーザー編集に対する行レベルのロールバックとコミットを実装する方法の具体例を示します。  
  
 [Windows フォーム DataGridView コントロールでの Just\-In\-Time データ読み込みによる仮想モードの実装](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 データを要求時に読み込む方法について説明します。この方法は、クライアント メモリに格納できないくらい多くのデータを表示しなければならないときに役立ちます。  
  
## 関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView> コントロールの参照ドキュメントを提供します。  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> プロパティの参照ドキュメントを提供します。  
  
## 参照  
 [DataGridView コントロール](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)   
 [Windows フォーム DataGridView コントロールでのデータ表示モード](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)