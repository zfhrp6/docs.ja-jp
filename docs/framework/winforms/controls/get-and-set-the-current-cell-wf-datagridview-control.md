---
title: "方法 : Windows フォーム DataGridView コントロールの現在のセルを取得および設定する | Microsoft Docs"
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
  - "セル, 取得と設定 (現在の)"
  - "DataGridView コントロール [Windows フォーム], 取得 (現在のセルを)"
  - "DataGridView コントロール [Windows フォーム], 設定 (現在のセルを)"
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : Windows フォーム DataGridView コントロールの現在のセルを取得および設定する
多くの場合、<xref:System.Windows.Forms.DataGridView> との対話では、現在アクティブなセルをプログラムで検出する必要があります。  また、現在のセルを変更する必要もあります。  これらのタスクは <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> プロパティを使用して実行できます。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> プロパティが `false` に設定されている行または列には現在のセルを設定できません。  
  
 <xref:System.Windows.Forms.DataGridView> コントロールの選択モードによっては、現在のセルを変更することで選択内容が変わることがあります。  詳細については、「[Windows フォーム DataGridView コントロールの選択モード](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
### 現在のセルをプログラムで取得するには  
  
-   <xref:System.Windows.Forms.DataGridView> コントロールの <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> プロパティを使用します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### 現在のセルをプログラムで設定するには  
  
-   <xref:System.Windows.Forms.DataGridView> コントロールの <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> プロパティを設定します。  次のコード例では、現在のセルは行 0、列 1 に設定されています。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   `getCurrentCellButton` という名前と `setCurrentCellButton` という名前の <xref:System.Windows.Forms.Button> コントロール。  [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] では、各ボタンの <xref:System.Windows.Forms.Control.Click> イベントをプログラム例の関連付けられているイベント ハンドラーに結合する必要があります。  
  
-   `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
-   <xref:System?displayProperty=fullName> アセンブリおよび <xref:System.Windows.Forms?displayProperty=fullName> アセンブリへの参照。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=fullName>   
 [Windows フォーム DataGridView コントロールでの列、行、およびセルの基本機能](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールの選択モード](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)