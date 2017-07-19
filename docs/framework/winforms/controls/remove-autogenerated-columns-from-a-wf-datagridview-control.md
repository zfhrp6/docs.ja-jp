---
title: "方法 : Windows フォーム DataGridView コントロールから自動生成された列を削除する | Microsoft Docs"
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
  - "列 [Windows フォーム], 削除"
  - "DataGridView コントロール [Windows フォーム], 削除 (列を)"
ms.assetid: 92e28d98-95a3-446c-9150-41b7c7e5be15
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : Windows フォーム DataGridView コントロールから自動生成された列を削除する
データ ソースのデータに基づいて列を自動生成するように <xref:System.Windows.Forms.DataGridView> コントロールが設定されている場合、特定の列を任意に選択して省略できます。  この省略は、<xref:System.Windows.Forms.DataGridView.Columns%2A> コレクションの <xref:System.Windows.Forms.DataGridViewColumnCollection.Remove%2A> メソッドを呼び出して実行できます。  これ以外に、<xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> プロパティを `false` に設定することによってもビューから列を非表示にできます。  この手法は、特定の条件で非表示の列を表示する場合や、列内のデータに非表示にしたままアクセスする必要がある場合に便利です。  
  
### 自動生成された列を削除するには  
  
-   <xref:System.Windows.Forms.DataGridView.Columns%2A> コレクションの <xref:System.Windows.Forms.DataGridViewColumnCollection.Remove%2A> メソッドを呼び出します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#111](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#111)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#111](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#111)]  
  
### 自動生成された列を非表示するには  
  
-   列の <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> プロパティを `false` に設定します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#112](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#112)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#112](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#112)]  
  
## 使用例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#110)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#110)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   Northwind サンプルデータベースの `Customers` テーブルなど、`Fax` 列と `CustomerID` 列を含むテーブルにバインドされている `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
-   <xref:System?displayProperty=fullName> アセンブリおよび <xref:System.Windows.Forms?displayProperty=fullName> アセンブリへの参照。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumnCollection.Remove%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=fullName>   
 [Windows フォーム DataGridView コントロールでのデータの表示](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)