---
title: "方法 : 行テンプレートを使用して Windows フォーム DataGridView コントロールの行をカスタマイズする | Microsoft Docs"
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
  - "データ グリッド, カスタマイズ (行を)"
  - "DataGridView コントロール [Windows フォーム], カスタマイズ (行を)"
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : 行テンプレートを使用して Windows フォーム DataGridView コントロールの行をカスタマイズする
<xref:System.Windows.Forms.DataGridView> コントロールは、コントロールに追加するすべての行の基礎として行テンプレートを使用します。これは、データ バインディングを使用する場合にも、使用する既存の行を指定せずに <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=fullName> メソッドを呼び出す場合にも当てはまります。  
  
 行テンプレートを使用すると、<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> プロパティを使用した場合よりも、行の外観および動作を厳密に制御できます。  行テンプレートでは、<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A> を含む任意の <xref:System.Windows.Forms.DataGridViewRow> プロパティを設定できます。  
  
 特定の効果を実現するために、行テンプレートを使用しなければならないこともあります。  たとえば、行の高さの情報は <xref:System.Windows.Forms.DataGridViewCellStyle> に格納できないため、行テンプレートを使用して、すべての行の既定の高さを変更する必要があります。  行テンプレートは、<xref:System.Windows.Forms.DataGridViewRow> から派生した独自のクラスを作成して、新しい行をコントロールに追加するときにカスタム型を使用する場合にも役立ちます。  
  
> [!NOTE]
>  行テンプレートを使用できるのは、行を追加する場合だけです。  既存の行は、行テンプレートを変更することによって変更できません。  
  
### 行テンプレートを使用するには  
  
-   <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=fullName> プロパティから取得したオブジェクトの各プロパティを設定します。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
-   <xref:System?displayProperty=fullName> アセンブリ、<xref:System.Drawing?displayProperty=fullName> アセンブリ、および <xref:System.Windows.Forms?displayProperty=fullName> アセンブリへの参照。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewCellStyle>   
 <xref:System.Windows.Forms.DataGridViewRow>   
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=fullName>   
 [Windows フォームの DataGridView コントロールの基本的な書式設定およびスタイル設定](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールでのセルのスタイル](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)