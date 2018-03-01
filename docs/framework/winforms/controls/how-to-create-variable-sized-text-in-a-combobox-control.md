---
title: "方法 : ComboBox コントロールにサイズ変更可能なテキストを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- vb
helpviewer_keywords:
- text [Windows Forms], drawing in combo boxes
- examples [Windows Forms], ComboBox control
- combo boxes [Windows Forms], drawing text
- ComboBox control [Windows Forms], examples [C#]
- ComboBox control [Windows Forms], drawing custom text
ms.assetid: ce39b9ea-e626-49fe-bd5a-f567f6d157df
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b8658b51515d8d3934613b40a8d4bec0ab9bf618
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-variable-sized-text-in-a-combobox-control"></a><span data-ttu-id="6dbc6-102">方法 : ComboBox コントロールにサイズ変更可能なテキストを作成する</span><span class="sxs-lookup"><span data-stu-id="6dbc6-102">How to: Create Variable Sized Text in a ComboBox Control</span></span>
<span data-ttu-id="6dbc6-103">この例は、内のテキストのカスタムの描画、<xref:System.Windows.Forms.ComboBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="6dbc6-103">This example demonstrates custom drawing of text in a <xref:System.Windows.Forms.ComboBox> control.</span></span> <span data-ttu-id="6dbc6-104">項目は、特定の条件を満たしている場合を大きいフォントで描画され、赤になっています。</span><span class="sxs-lookup"><span data-stu-id="6dbc6-104">When an item meets a certain criteria, it is drawn in a larger font and turned red.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6dbc6-105">例</span><span class="sxs-lookup"><span data-stu-id="6dbc6-105">Example</span></span>  
  
```vb  
Private Sub ComboBox1_MeasureItem(ByVal sender As Object, ByVal e As _  
System.Windows.Forms.MeasureItemEventArgs) Handles ComboBox1.MeasureItem  
    Dim bFont As New Font("Arial", 8, FontStyle.Bold)  
    Dim lFont As New Font("Arial", 12, FontStyle.Bold)  
    Dim siText As SizeF  
  
    If ComboBox1.Items().Item(e.Index) = "Two" Then  
        siText = e.Graphics.MeasureString(ComboBox1.Items().Item(e.Index), _  
lFont)  
    Else  
        siText = e.Graphics.MeasureString(ComboBox1.Items().Item(e.Index), bFont)  
    End If  
  
    e.ItemHeight = siText.Height  
    e.ItemWidth = siText.Width  
End Sub  
  
Private Sub ComboBox1_DrawItem(ByVal sender As Object, ByVal e As _  
System.Windows.Forms.DrawItemEventArgs) Handles ComboBox1.DrawItem  
    Dim g As Graphics = e.Graphics  
    Dim bFont As New Font("Arial", 8, FontStyle.Bold)  
    Dim lFont As New Font("Arial", 12, FontStyle.Bold)  
  
    If ComboBox1.Items().Item(e.Index) = "Two" Then  
        g.DrawString(ComboBox1.Items.Item(e.Index), lfont, Brushes.Red, _  
e.Bounds.X, e.Bounds.Y)  
    Else  
        g.DrawString(ComboBox1.Items.Item(e.Index), bFont, Brushes.Black, e.Bounds.X, e.Bounds.Y)  
    End If  
End Sub  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6dbc6-106">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="6dbc6-106">Compiling the Code</span></span>  
 <span data-ttu-id="6dbc6-107">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6dbc6-107">This example requires:</span></span>  
  
-   <span data-ttu-id="6dbc6-108">Windows フォームです。</span><span class="sxs-lookup"><span data-stu-id="6dbc6-108">A Windows form.</span></span>  
  
-   <span data-ttu-id="6dbc6-109">A<xref:System.Windows.Forms.ComboBox>という名前のコントロール`ListBox1`で 3 つの項目を含む、<xref:System.Windows.Forms.ComboBox.Items%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="6dbc6-109">A <xref:System.Windows.Forms.ComboBox> control named `ListBox1` with three items in the <xref:System.Windows.Forms.ComboBox.Items%2A> property.</span></span> <span data-ttu-id="6dbc6-110">この例では、3 つの項目の名前は`"One", Two", and Three"`します。</span><span class="sxs-lookup"><span data-stu-id="6dbc6-110">In this example, the three items are named `"One", Two", and Three"`.</span></span> <span data-ttu-id="6dbc6-111"><xref:System.Windows.Forms.ComboBox.DrawMode%2A>プロパティ`ComboBox1`に設定する必要があります<xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>です。</span><span class="sxs-lookup"><span data-stu-id="6dbc6-111">The <xref:System.Windows.Forms.ComboBox.DrawMode%2A> property of `ComboBox1` must be set to <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6dbc6-112">この手法に適用も、<xref:System.Windows.Forms.ListBox>コントロール — 代わりに使用することができます、<xref:System.Windows.Forms.ListBox>の<xref:System.Windows.Forms.ComboBox>です。</span><span class="sxs-lookup"><span data-stu-id="6dbc6-112">This technique is also applicable to the <xref:System.Windows.Forms.ListBox> control — you can substitute a <xref:System.Windows.Forms.ListBox> for the <xref:System.Windows.Forms.ComboBox>.</span></span>  
  
-   <span data-ttu-id="6dbc6-113"><xref:System.Windows.Forms?displayProperty=nameWithType> 名前空間と <xref:System.Drawing?displayProperty=nameWithType> 名前空間への参照。</span><span class="sxs-lookup"><span data-stu-id="6dbc6-113">References to the <xref:System.Windows.Forms?displayProperty=nameWithType> and <xref:System.Drawing?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dbc6-114">参照</span><span class="sxs-lookup"><span data-stu-id="6dbc6-114">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox.DrawItem>  
 <xref:System.Windows.Forms.DrawItemEventArgs>  
 <xref:System.Windows.Forms.ComboBox.MeasureItem>  
 [<span data-ttu-id="6dbc6-115">組み込みのオーナー描画サポートを備えたコントロール</span><span class="sxs-lookup"><span data-stu-id="6dbc6-115">Controls with Built-In Owner-Drawing Support</span></span>](../../../../docs/framework/winforms/controls/controls-with-built-in-owner-drawing-support.md)  
 [<span data-ttu-id="6dbc6-116">ListBox コントロール</span><span class="sxs-lookup"><span data-stu-id="6dbc6-116">ListBox Control</span></span>](../../../../docs/framework/winforms/controls/listbox-control-windows-forms.md)  
 [<span data-ttu-id="6dbc6-117">ComboBox コントロール</span><span class="sxs-lookup"><span data-stu-id="6dbc6-117">ComboBox Control</span></span>](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)
