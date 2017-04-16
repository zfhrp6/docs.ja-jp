---
title: "方法 : ITypedList インターフェイスを実装する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "BindingList(Of T) クラス"
  - "データ バインド, 実装"
  - "IBindingList インターフェイス"
  - "ITypedList インターフェイス"
ms.assetid: 834cc15c-50bc-4a8b-a610-313d6a217357
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : ITypedList インターフェイスを実装する
バインドできるリストのスキーマを検出できるようにするには、<xref:System.ComponentModel.ITypedList> インターフェイスを実装します。  
  
## 使用例  
 <xref:System.ComponentModel.ITypedList> インターフェイスを実装する方法を次のコード例に示します。  `SortableBindingList` というジェネリック型は、<xref:System.ComponentModel.BindingList%601> クラスから派生し、<xref:System.ComponentModel.ITypedList> インターフェイスを実装します。  `Customer` という単純なクラスは、<xref:System.Windows.Forms.DataGridView> コントロールのヘッダーにバインドされるデータを提供します。  
  
 [!code-csharp[System.ComponentModel.ITypedList#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/SortableBindingList.cs#1)]
 [!code-vb[System.ComponentModel.ITypedList#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/SortableBindingList.vb#1)]  
  
 [!code-csharp[System.ComponentModel.ITypedList#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/Customer.cs#10)]
 [!code-vb[System.ComponentModel.ITypedList#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/Customer.vb#10)]  
  
 [!code-csharp[System.ComponentModel.ITypedList#100](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/Form1.cs#100)]
 [!code-vb[System.ComponentModel.ITypedList#100](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/Form1.vb#100)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   System.Drawing アセンブリと System.Windows.Forms アセンブリへの参照。  
  
## 参照  
 <xref:System.ComponentModel.ITypedList>   
 <xref:System.ComponentModel.BindingList%601>   
 <xref:System.ComponentModel.IBindingList>   
 [データ連結と Windows フォーム](../../../docs/framework/winforms/data-binding-and-windows-forms.md)