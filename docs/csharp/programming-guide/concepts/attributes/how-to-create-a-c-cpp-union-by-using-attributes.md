---
title: "方法: 属性を使用して C-C++ の共用体を作成する (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4532829080d994cf4cec92d64a12e3bf1890dc6a
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a><span data-ttu-id="4b40b-102">方法: 属性を使用して C/C++ の共用体を作成する (C#)</span><span class="sxs-lookup"><span data-stu-id="4b40b-102">How to: Create a C/C++ Union by Using Attributes (C#)</span></span>
<span data-ttu-id="4b40b-103">属性を使用すると、構造体のメモリ内での配置をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="4b40b-103">By using attributes you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="4b40b-104">たとえば、`StructLayout(LayoutKind.Explicit)` 属性と `FieldOffset` 属性を使用すると、C/C++ の共用体と呼ばれるものを作成できます。</span><span class="sxs-lookup"><span data-stu-id="4b40b-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b40b-105">例</span><span class="sxs-lookup"><span data-stu-id="4b40b-105">Example</span></span>  
 <span data-ttu-id="4b40b-106">このコード セグメントでは、`TestUnion` のすべてのフィールドがメモリ内の同じ場所で開始されます。</span><span class="sxs-lookup"><span data-stu-id="4b40b-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>  
  
```csharp  
// Add a using directive for System.Runtime.InteropServices.  
  
       [System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]  
       struct TestUnion  
       {  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public int i;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public double d;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public char c;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public byte b;  
       }  
```  
  
## <a name="example"></a><span data-ttu-id="4b40b-107">例</span><span class="sxs-lookup"><span data-stu-id="4b40b-107">Example</span></span>  
 <span data-ttu-id="4b40b-108">次の例でも、明示的に設定されたさまざまな場所でフィールドが開始されます。</span><span class="sxs-lookup"><span data-stu-id="4b40b-108">The following is another example where fields start at different explicitly set locations.</span></span>  
  
```csharp  
// Add a using directive for System.Runtime.InteropServices.  
  
       [System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]  
       struct TestExplicit  
       {  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public long lg;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public int i1;  
  
           [System.Runtime.InteropServices.FieldOffset(4)]  
           public int i2;  
  
           [System.Runtime.InteropServices.FieldOffset(8)]  
           public double d;  
  
           [System.Runtime.InteropServices.FieldOffset(12)]  
           public char c;  
  
           [System.Runtime.InteropServices.FieldOffset(14)]  
           public byte b;  
       }  
```  
  
 <span data-ttu-id="4b40b-109">2 つの整数フィールド、`i1` および `i2` は、`lg` と同じメモリ位置を共有します。</span><span class="sxs-lookup"><span data-stu-id="4b40b-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="4b40b-110">このような構造体配置の制御は、プラットフォームを呼び出すときに便利です。</span><span class="sxs-lookup"><span data-stu-id="4b40b-110">This sort of control over struct layout is useful when using platform invocation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b40b-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="4b40b-111">See Also</span></span>  
 <span data-ttu-id="4b40b-112"><xref:System.Reflection></span><span class="sxs-lookup"><span data-stu-id="4b40b-112"><xref:System.Reflection></span></span>   
 <span data-ttu-id="4b40b-113"><xref:System.Attribute></span><span class="sxs-lookup"><span data-stu-id="4b40b-113"><xref:System.Attribute></span></span>   
 <span data-ttu-id="4b40b-114">[C# プログラミング ガイド](../../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="4b40b-114">[C# Programming Guide](../../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="4b40b-115">[属性](https://msdn.microsoft.com/library/5x6cd29c) </span><span class="sxs-lookup"><span data-stu-id="4b40b-115">[Attributes](https://msdn.microsoft.com/library/5x6cd29c) </span></span>  
 <span data-ttu-id="4b40b-116">[リフレクション (C#)](../../../../csharp/programming-guide/concepts/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="4b40b-116">[Reflection (C#)](../../../../csharp/programming-guide/concepts/reflection.md) </span></span>  
 <span data-ttu-id="4b40b-117">[属性 (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md) </span><span class="sxs-lookup"><span data-stu-id="4b40b-117">[Attributes (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md) </span></span>  
 <span data-ttu-id="4b40b-118">[カスタム属性の作成 (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="4b40b-118">[Creating Custom Attributes (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md) </span></span>  
 [<span data-ttu-id="4b40b-119">リフレクションを使用した属性へのアクセス (C#)</span><span class="sxs-lookup"><span data-stu-id="4b40b-119">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)

