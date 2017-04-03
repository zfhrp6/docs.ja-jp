---
title: "方法: 属性を使用して C/C++ の共用体を作成する (C#) | Microsoft Docs"
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: dd6bc60dfd1c6146d8fa72abdcfc6a00006817aa
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a>方法: 属性を使用して C/C++ の共用体を作成する (C#)
属性を使用すると、構造体のメモリ内での配置をカスタマイズできます。 たとえば、`StructLayout(LayoutKind.Explicit)` 属性と `FieldOffset` 属性を使用すると、C/C++ の共用体と呼ばれるものを作成できます。  
  
## <a name="example"></a>例  
 このコード セグメントでは、`TestUnion` のすべてのフィールドがメモリ内の同じ場所で開始されます。  
  
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
  
## <a name="example"></a>例  
 次の例でも、明示的に設定されたさまざまな場所でフィールドが開始されます。  
  
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
  
 2 つの整数フィールド、`i1` および `i2` は、`lg` と同じメモリ位置を共有します。 このような構造体配置の制御は、プラットフォームを呼び出すときに便利です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Reflection>   
 <xref:System.Attribute>   
 [C# プログラミング ガイド](../../../../csharp/programming-guide/index.md)   
 [属性](https://msdn.microsoft.com/library/5x6cd29c)   
 [リフレクション (C#)](../../../../csharp/programming-guide/concepts/reflection.md)   
 [属性 (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)   
 [カスタム属性の作成 (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)   
 [リフレクションを使用した属性へのアクセス (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
