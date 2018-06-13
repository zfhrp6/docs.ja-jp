---
title: '方法 : IListSource インターフェイスを実装する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], implementing
- IListSource interface
ms.assetid: 63ce27aa-2e23-4fbd-8228-0c1726f6c421
ms.openlocfilehash: 3b580208e003a1706cca8e9fdff4ab374b7193ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539417"
---
# <a name="how-to-implement-the-ilistsource-interface"></a><span data-ttu-id="d7a56-102">方法 : IListSource インターフェイスを実装する</span><span class="sxs-lookup"><span data-stu-id="d7a56-102">How to: Implement the IListSource Interface</span></span>
<span data-ttu-id="d7a56-103">実装、<xref:System.ComponentModel.IListSource>インターフェイスを実装しないバインド可能なクラスを作成する<xref:System.Collections.IList>が、別の場所からリストを提供します。</span><span class="sxs-lookup"><span data-stu-id="d7a56-103">Implement the <xref:System.ComponentModel.IListSource> interface to create a bindable class that does not implement <xref:System.Collections.IList> but instead provides a list from another location.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7a56-104">例</span><span class="sxs-lookup"><span data-stu-id="d7a56-104">Example</span></span>  
 <span data-ttu-id="d7a56-105">次のコード例は、実装する方法を示します、<xref:System.ComponentModel.IListSource>インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="d7a56-105">The following code example demonstrates how to implement the <xref:System.ComponentModel.IListSource> interface.</span></span> <span data-ttu-id="d7a56-106">という名前のコンポーネント`EmployeeListSource`公開、<xref:System.Collections.IList>を実装してデータ バインディング、<xref:System.ComponentModel.IListSource.GetList%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d7a56-106">A component named `EmployeeListSource` exposes an <xref:System.Collections.IList> for data binding by implementing the <xref:System.ComponentModel.IListSource.GetList%2A> method.</span></span>  
  
 [!code-csharp[System.ComponentModel.IListSource#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IListSource/CS/EmployeeListSource.cs#1)]
 [!code-vb[System.ComponentModel.IListSource#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IListSource/VB/EmployeeListSource.vb#1)]  
  
 [!code-csharp[System.ComponentModel.IListSource#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IListSource/CS/Employee.cs#10)]
 [!code-vb[System.ComponentModel.IListSource#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IListSource/VB/Employee.vb#10)]  
  
 [!code-csharp[System.ComponentModel.IListSource#100](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IListSource/CS/BusinessObjectBase.cs#100)]
 [!code-vb[System.ComponentModel.IListSource#100](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IListSource/VB/BusinessObjectBase.vb#100)]  
  
 [!code-csharp[System.ComponentModel.IListSource#1000](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IListSource/CS/Form1.cs#1000)]
 [!code-vb[System.ComponentModel.IListSource#1000](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IListSource/VB/Form1.vb#1000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d7a56-107">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="d7a56-107">Compiling the Code</span></span>  
 <span data-ttu-id="d7a56-108">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d7a56-108">This example requires:</span></span>  
  
-   <span data-ttu-id="d7a56-109">System.Drawing アセンブリおよび System.Windows.Forms アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="d7a56-109">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7a56-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="d7a56-110">See Also</span></span>  
 <xref:System.ComponentModel.IListSource>  
 <xref:System.ComponentModel.ITypedList>  
 <xref:System.ComponentModel.BindingList%601>  
 <xref:System.ComponentModel.IBindingList>  
 [<span data-ttu-id="d7a56-111">データ連結と Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="d7a56-111">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
