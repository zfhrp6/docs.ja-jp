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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3ff1686328630b233b25839c79d0009d48aab5ab
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a>方法: 属性 (Visual Basic) を使用して C/C++ の共用体を作成します。
属性を使用して、構造体のメモリ内のレイアウトをカスタマイズできます。 使用して C/C++ の共用体と呼ばれるものを作成するなど、`StructLayout(LayoutKind.Explicit)`と`FieldOffset`属性です。  
  
## <a name="example"></a>例  
 このコード セグメントは、すべてのフィールドの`TestUnion`メモリ内の同じ場所から開始します。  
  
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
 さまざまなフィールドの開始が明示的に場所を設定、別の例を次に示します。  
  
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
  
 2 つの整数フィールド`i1`と`i2`と同じメモリ位置を共有`lg`します。 このような構造体レイアウト コントロールは、プラットフォーム呼び出しを使用する場合に便利です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Reflection></xref:System.Reflection>   
 <xref:System.Attribute></xref:System.Attribute>   
 [Visual Basic のプログラミング ガイド](../../../../visual-basic/programming-guide/index.md)   
 [属性](https://msdn.microsoft.com/library/5x6cd29c)   
 [リフレクション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)   
 [属性 (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)   
 [カスタム属性 (Visual Basic) の作成](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)   
 [リフレクション (Visual Basic) を使用して属性へのアクセス](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
