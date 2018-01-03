---
title: "方法: 属性 (Visual Basic) を使用して C/C++ の共用体を作成します。"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 51d04c573e91a351c48edefebdb3d32fce1d306f
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a>方法: 属性 (Visual Basic) を使用して C/C++ の共用体を作成します。
属性を使用すると、構造体のメモリ内での配置をカスタマイズできます。 たとえば、`StructLayout(LayoutKind.Explicit)` 属性と `FieldOffset` 属性を使用すると、C/C++ の共用体と呼ばれるものを作成できます。  
  
## <a name="example"></a>例  
 このコード セグメントでは、`TestUnion` のすべてのフィールドがメモリ内の同じ場所で開始されます。  
  
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
  
## <a name="example"></a>例  
 次の例でも、明示的に設定されたさまざまな場所でフィールドが開始されます。  
  
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
  
 2 つの整数フィールド、`i1` および `i2` は、`lg` と同じメモリ位置を共有します。 このような構造体配置の制御は、プラットフォームを呼び出すときに便利です。  
  
## <a name="see-also"></a>参照  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [Visual Basic プログラミング ガイド](../../../../visual-basic/programming-guide/index.md)  
 [属性](../../../../standard/attributes/index.md)  
 [リフレクション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [属性 (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)  
 [カスタム属性の作成 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [リフレクションを使用した属性へのアクセス (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
