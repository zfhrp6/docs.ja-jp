---
title: "方法 : Windows フォーム DataGridView コントロールの編集モードを指定する | Microsoft Docs"
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
  - "データ グリッド, 編集モード"
  - "DataGridView コントロール [Windows フォーム], 編集モード"
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 方法 : Windows フォーム DataGridView コントロールの編集モードを指定する
既定では、ユーザーが現在の <xref:System.Windows.Forms.DataGridView> テキスト ボックス セルの内容を編集するには、セル内に入力するか、F2 キーを押します。  次の条件をすべて満たしている場合は、この操作によって、セルは編集モードになります。  
  
-   基になるデータ ソースが編集をサポートしている。  
  
-   <xref:System.Windows.Forms.DataGridView> コントロールが有効である。  
  
-   <xref:System.Windows.Forms.DataGridView.EditMode%2A> プロパティ値が <xref:System.Windows.Forms.DataGridViewEditMode> ではない。  
  
-   セル、行、列、およびコントロールの `ReadOnly` プロパティがすべて `false` に設定されている。  
  
 編集モードでは、ユーザーはセルの値を変更し、Enter キーを押して変更をコミットしたり、Esc キーを押してセルの値を元に戻したりできます。  
  
 現在のセルになったときにすぐに編集モードになるように <xref:System.Windows.Forms.DataGridView> コントロールを構成できます。  この場合、Enter キーと Esc キーの動作は変更されませんが、値をコミットした後や元に戻した後も、セルは編集モードのままです。  ユーザーがセル内に入力した場合や、F2 キーを押した場合にのみ、セルが編集モードになるようにコントロールを構成することもできます。  また、<xref:System.Windows.Forms.DataGridView.BeginEdit%2A> メソッドを呼び出す場合を除き、セルが編集モードにならないように構成することもできます。  
  
### DataGridView コントロールの編集モードを変更するには  
  
-   <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=fullName> プロパティに適切な <xref:System.Windows.Forms.DataGridViewEditMode> 列挙値を設定します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
-   <xref:System> アセンブリおよび <xref:System.Windows.Forms> アセンブリへの参照。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=fullName>   
 [Windows フォーム DataGridView コントロールでのデータ入力](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)