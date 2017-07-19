---
title: "方法 : Windows フォーム DataGridView コントロールの新しい行に既定値を指定する | Microsoft Docs"
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
  - "データ グリッド, 既定値 (新しい行の)"
  - "DataGridView コントロール [Windows フォーム], データ エントリ"
  - "DataGridView コントロール [Windows フォーム], 既定値 (新しい行の)"
  - "行, 指定 (既定値を)"
ms.assetid: 8d127963-d9f8-4e4e-9f7f-beb66688f1f2
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : Windows フォーム DataGridView コントロールの新しい行に既定値を指定する
新しく追加された行にアプリケーションが既定値を読み込むことでデータ入力を簡素化できます。  <xref:System.Windows.Forms.DataGridView> クラスを使用すると、<xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> イベントで既定値を読み込むことができます。  このイベントは、ユーザーが新しいレコード用の行を入力すると発生します。  コードでこのイベントを処理すると、任意のセルに任意に選択した値を読み込むことができます。  
  
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> イベントを使用して新しい行に既定値を指定する方法を次のコード例に示します。  
  
## 使用例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
-   一意の `CustomerID` 値を生成する `NewCustomerId` 関数。  
  
-   <xref:System?displayProperty=fullName> アセンブリおよび <xref:System.Windows.Forms?displayProperty=fullName> アセンブリへの参照。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=fullName>   
 [Windows フォーム DataGridView コントロールでのデータ入力](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールにおける新規レコード行の使用](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)