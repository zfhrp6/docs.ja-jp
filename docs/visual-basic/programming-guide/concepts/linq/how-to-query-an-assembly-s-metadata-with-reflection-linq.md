---
title: "方法: リフレクション (LINQ) (Visual Basic) を使用してアセンブリのメタデータを照会する |Microsoft ドキュメント"
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
ms.assetid: 53caa336-ab83-4181-b0f6-5c87c5f9e4ee
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7c1bc26d7b23135dd45ad58ea0bd2510b7157448
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-query-an-assembly39s-metadata-with-reflection-linq-visual-basic"></a>方法: リフレクション (LINQ) (Visual Basic) を使用してアセンブリのメタデータを照会します。
次の例では、指定した検索条件に一致するメソッドについてのメタデータを取得する LINQ をリフレクションを使用して使用する方法を示します。 ここで、クエリでは、配列などの列挙可能な型を返すアセンブリのすべてのメソッドの名前は見つけします。  
  
## <a name="example"></a>例  
  
```vb  
Imports System.Reflection  
Imports System.IO  
Imports System.Linq  
Module Module1  
  
    Sub Main()  
        Dim asmbly As Assembly =   
            Assembly.Load("System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken= b77a5c561934e089")  
  
        Dim pubTypesQuery = From type In asmbly.GetTypes()   
                            Where type.IsPublic   
                            From method In type.GetMethods()   
                            Where method.ReturnType.IsArray = True   
                            Let name = method.ToString()   
                            Let typeName = type.ToString()   
                            Group name By typeName Into methodNames = Group  
  
        Console.WriteLine("Getting ready to iterate")  
        For Each item In pubTypesQuery  
            Console.WriteLine(item.methodNames)  
  
            For Each type In item.methodNames  
                Console.WriteLine(" " & type)  
            Next  
        Next  
        Console.ReadKey()  
    End Sub  
  
End Module  
```  
  
 例では、<xref:System.Reflection.Assembly.GetTypes%2A>を指定したアセンブリで型の配列を返すメソッド</xref:System.Reflection.Assembly.GetTypes%2A>。 [Where 句](../../../../visual-basic/language-reference/queries/where-clause.md)パブリック型のみが返されるようにフィルターを適用します。 使用して各パブリック型のサブクエリが生成される、<xref:System.Reflection.MethodInfo>から返される配列、<xref:System.Type.GetMethods%2A>を呼び出す</xref:System.Type.GetMethods%2A></xref:System.Reflection.MethodInfo>。 これらの結果は戻り値の型は<xref:System.Collections.Generic.IEnumerable%601>。</xref:System.Collections.Generic.IEnumerable%601>を実装する型か、または配列メソッドのみを返すフィルター処理します。 最後に、これらの結果は、キーとして、型名を使用して、グループ化されます。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 .NET Framework version 3.5 またはそれ以上、System.Core.dll への参照を対象とするプロジェクトを作成し、 `Imports` System.Linq 名前空間のステートメントです。  
  
## <a name="see-also"></a>関連項目  
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
