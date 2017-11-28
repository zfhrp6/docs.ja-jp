---
title: "方法 : ITypedList インターフェイスを実装する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ITypedList interface
- BindingList(Of T) class
- data binding [Windows Forms], implementing
- IBindingList interface
ms.assetid: 834cc15c-50bc-4a8b-a610-313d6a217357
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 95888fc5c0df31529db429ead0e7d3e342f9a6e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-the-itypedlist-interface"></a>方法 : ITypedList インターフェイスを実装する
実装、<xref:System.ComponentModel.ITypedList>バインド可能な一覧については、スキーマの検出を有効にするインターフェイスです。  
  
## <a name="example"></a>例  
 次のコード例は、実装する方法を示します、<xref:System.ComponentModel.ITypedList>インターフェイスです。 という名前のジェネリック型`SortableBindingList`から派生した、<xref:System.ComponentModel.BindingList%601>クラスと実装、<xref:System.ComponentModel.ITypedList>インターフェイスです。 という名前の単純なクラス`Customer`のヘッダーにバインドされているデータを提供する<xref:System.Windows.Forms.DataGridView>コントロール。  
  
 [!code-csharp[System.ComponentModel.ITypedList#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/SortableBindingList.cs#1)]
 [!code-vb[System.ComponentModel.ITypedList#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/SortableBindingList.vb#1)]  
  
 [!code-csharp[System.ComponentModel.ITypedList#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/Customer.cs#10)]
 [!code-vb[System.ComponentModel.ITypedList#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/Customer.vb#10)]  
  
 [!code-csharp[System.ComponentModel.ITypedList#100](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/Form1.cs#100)]
 [!code-vb[System.ComponentModel.ITypedList#100](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System.Drawing アセンブリおよび System.Windows.Forms アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ComponentModel.ITypedList>  
 <xref:System.ComponentModel.BindingList%601>  
 <xref:System.ComponentModel.IBindingList>  
 [データ連結と Windows フォーム](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
