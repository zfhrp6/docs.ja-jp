---
title: "方法: 属性 (Visual Basic) を使用して C/C++ の共用体を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 195dc0c64cb01e38ede0b7c34c30ca7912aea685
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a><span data-ttu-id="9a511-102">方法: 属性 (Visual Basic) を使用して C/C++ の共用体を作成します。</span><span class="sxs-lookup"><span data-stu-id="9a511-102">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>
<span data-ttu-id="9a511-103">属性を使用して、構造体のメモリ内のレイアウトをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="9a511-103">By using attributes you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="9a511-104">使用して C/C++ の共用体と呼ばれるものを作成するなど、`StructLayout(LayoutKind.Explicit)`と`FieldOffset`属性です。</span><span class="sxs-lookup"><span data-stu-id="9a511-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a511-105">例</span><span class="sxs-lookup"><span data-stu-id="9a511-105">Example</span></span>  
 <span data-ttu-id="9a511-106">このコード セグメントは、すべてのフィールドの`TestUnion`メモリ内の同じ場所から開始します。</span><span class="sxs-lookup"><span data-stu-id="9a511-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>  
  
```vb  
' Add an Imports statement for System.Runtime.InteropServices.  
  
<System.Runtime.InteropServices.StructLayout(   
      System.Runtime.InteropServices.LayoutKind.Explicit)>   
Structure TestUnion  
    <System.Runtime.InteropServices.FieldOffset(0)>   
    Public i As Integer  
  
    <System.Runtime.InteropServices.FieldOffset(0)>   
    Public d As Double  
  
    <System.Runtime.InteropServices.FieldOffset(0)>   
    Public c As Char  
  
    <System.Runtime.InteropServices.FieldOffset(0)>   
    Public b As Byte  
End Structure  
```  
  
## <a name="example"></a><span data-ttu-id="9a511-107">例</span><span class="sxs-lookup"><span data-stu-id="9a511-107">Example</span></span>  
 <span data-ttu-id="9a511-108">さまざまなフィールドの開始が明示的に場所を設定、別の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9a511-108">The following is another example where fields start at different explicitly set locations.</span></span>  
  
```vb  
' Add an Imports statement for System.Runtime.InteropServices.  
  
 <System.Runtime.InteropServices.StructLayout(   
      System.Runtime.InteropServices.LayoutKind.Explicit)>   
Structure TestExplicit  
     <System.Runtime.InteropServices.FieldOffset(0)>   
     Public lg As Long  
  
     <System.Runtime.InteropServices.FieldOffset(0)>   
     Public i1 As Integer  
  
     <System.Runtime.InteropServices.FieldOffset(4)>   
     Public i2 As Integer  
  
     <System.Runtime.InteropServices.FieldOffset(8)>   
     Public d As Double  
  
     <System.Runtime.InteropServices.FieldOffset(12)>   
     Public c As Char  
  
     <System.Runtime.InteropServices.FieldOffset(14)>   
     Public b As Byte  
 End Structure  
```  
  
 <span data-ttu-id="9a511-109">2 つの整数フィールド`i1`と`i2`と同じメモリ位置を共有`lg`します。</span><span class="sxs-lookup"><span data-stu-id="9a511-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="9a511-110">このような構造体レイアウト コントロールは、プラットフォーム呼び出しを使用する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="9a511-110">This sort of control over struct layout is useful when using platform invocation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a511-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a511-111">See Also</span></span>  
 <span data-ttu-id="9a511-112"><xref:System.Reflection></xref:System.Reflection></span><span class="sxs-lookup"><span data-stu-id="9a511-112"><xref:System.Reflection></span></span>   
 <span data-ttu-id="9a511-113"><xref:System.Attribute></xref:System.Attribute></span><span class="sxs-lookup"><span data-stu-id="9a511-113"><xref:System.Attribute></span></span>   
<span data-ttu-id="9a511-114"> [Visual Basic のプログラミング ガイド](../../../../visual-basic/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9a511-114"> [Visual Basic Programming Guide](../../../../visual-basic/programming-guide/index.md) </span></span>  
<span data-ttu-id="9a511-115"> [属性](https://msdn.microsoft.com/library/5x6cd29c) </span><span class="sxs-lookup"><span data-stu-id="9a511-115"> [Attributes](https://msdn.microsoft.com/library/5x6cd29c) </span></span>  
<span data-ttu-id="9a511-116"> [リフレクション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="9a511-116"> [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span></span>  
<span data-ttu-id="9a511-117"> [属性 (Visual Basic)](../../../../visual-basic/language-reference/attributes.md) </span><span class="sxs-lookup"><span data-stu-id="9a511-117"> [Attributes (Visual Basic)](../../../../visual-basic/language-reference/attributes.md) </span></span>  
<span data-ttu-id="9a511-118"> [カスタム属性 (Visual Basic) の作成](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="9a511-118"> [Creating Custom Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md) </span></span>  
<span data-ttu-id="9a511-119"> [リフレクション (Visual Basic) を使用して属性へのアクセス](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="9a511-119"> [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)</span></span>
