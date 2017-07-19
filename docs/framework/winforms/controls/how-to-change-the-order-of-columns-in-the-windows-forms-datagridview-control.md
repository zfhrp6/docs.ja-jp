---
title: "方法 : Windows フォーム DataGridView コントロールの列の順序を変更する | Microsoft Docs"
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
  - "列 [Windows フォーム], 変更 (順序を)"
  - "データ グリッド, 変更 (列の順序を)"
  - "DataGridView コントロール [Windows フォーム], 列の順序"
ms.assetid: 5e9ac3bc-b0f0-48cb-a3d5-b005af905395
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 方法 : Windows フォーム DataGridView コントロールの列の順序を変更する
<xref:System.Windows.Forms.DataGridView> を使用してデータをデータ ソースから表示する場合、データ ソースのスキーマの列が、表示したい順序で表示されないことがあります。  <xref:System.Windows.Forms.DataGridViewColumn> クラスの <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> プロパティを使用して、列の表示順序を変更できます。  
  
 次のコード例は、Northwind サンプル データベース内の Customers テーブルにバインドするときに自動的に生成される列のいくつかを再配置します。  <xref:System.Windows.Forms.DataGridView> コントロールをデータベース テーブルにバインドする方法の詳細については、「[方法 : データを Windows フォーム DataGridView コントロールにバインドする](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)」を参照してください。  
  
 Visual Studio では、このタスクに対するサポートが用意されています。  「[方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列の順序を変更する](http://msdn.microsoft.com/library/hb1dk7ax\(v=vs.110\))」も参照してください。  
  
## 使用例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#040](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#040)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#040](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#040)]  
  
## コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   Northwind サンプル データベース内の `Customers` テーブルなど、示されている列の名前を持つテーブルにバインドされた、`customersDataGridView` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
-   <xref:System?displayProperty=fullName>、<xref:System.Windows.Forms?displayProperty=fullName>、<xref:System.Data?displayProperty=fullName>、および <xref:System.Xml?displayProperty=fullName> の各アセンブリへの参照。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewColumn>   
 <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=fullName>   
 [Windows フォーム DataGridView コントロールでのデータの表示](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)   
 [方法 : データを Windows フォーム DataGridView コントロールにバインドする](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)