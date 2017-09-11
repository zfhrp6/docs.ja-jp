---
title: "リフレクション (Visual Basic) を使用して属性へのアクセス |Microsoft ドキュメント"
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
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ac1e017ae13fc1291fd41e5747171160a9d70238
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a><span data-ttu-id="0459a-102">リフレクション (Visual Basic) を使用して属性へのアクセス</span><span class="sxs-lookup"><span data-stu-id="0459a-102">Accessing Attributes by Using Reflection (Visual Basic)</span></span>
<span data-ttu-id="0459a-103">その情報を取得、およびその操作方法がないほとんどの値のカスタム属性を定義し、ソース コード内に配置できることになります。</span><span class="sxs-lookup"><span data-stu-id="0459a-103">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="0459a-104">リフレクションを使用するには、カスタム属性で定義されている情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="0459a-104">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="0459a-105">重要なメソッドは`GetCustomAttributes`実行時に相当するソース コードの属性であるオブジェクトの配列が返されます。</span><span class="sxs-lookup"><span data-stu-id="0459a-105">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="0459a-106">このメソッドには、いくつかのオーバー ロードされたバージョンがあります。</span><span class="sxs-lookup"><span data-stu-id="0459a-106">This method has several overloaded versions.</span></span> <span data-ttu-id="0459a-107">詳細については、 <xref:System.Attribute>。</xref:System.Attribute>を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0459a-107">For more information, see <xref:System.Attribute>.</span></span>  
  
 <span data-ttu-id="0459a-108">などの属性の指定:</span><span class="sxs-lookup"><span data-stu-id="0459a-108">An attribute specification such as:</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 <span data-ttu-id="0459a-109">概念的にはこれと同じです。</span><span class="sxs-lookup"><span data-stu-id="0459a-109">is conceptually equivalent to this:</span></span>  
  
```vb  
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")  
anonymousAuthorObject.version = 1.1  
```  
  
 <span data-ttu-id="0459a-110">ただし、コードをまで実行されず`SampleClass`の属性の照会します。</span><span class="sxs-lookup"><span data-stu-id="0459a-110">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="0459a-111">呼び出す`GetCustomAttributes`に`SampleClass`により、`Author`オブジェクトを構築しても、上記のように初期化します。</span><span class="sxs-lookup"><span data-stu-id="0459a-111">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="0459a-112">その他の属性をクラスには、その他の属性のオブジェクトが同様に構築されます。</span><span class="sxs-lookup"><span data-stu-id="0459a-112">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="0459a-113">`GetCustomAttributes`戻ります、`Author`オブジェクトと配列内の他の属性オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="0459a-113">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="0459a-114">この配列を反復処理することができますし、各配列要素の種類に基づいて適用された属性を確認し、属性のオブジェクトから情報を抽出します。</span><span class="sxs-lookup"><span data-stu-id="0459a-114">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0459a-115">例</span><span class="sxs-lookup"><span data-stu-id="0459a-115">Example</span></span>  
 <span data-ttu-id="0459a-116">完全な例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0459a-116">Here is a complete example.</span></span> <span data-ttu-id="0459a-117">カスタム属性が定義されている、複数のエンティティに適用され、リフレクションを使用して取得します。</span><span class="sxs-lookup"><span data-stu-id="0459a-117">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>  
  
```vb  
' Multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
    Private name As String  
    Public version As Double  
    Sub New(ByVal authorName As String)  
        name = authorName  
  
        ' Default value  
        version = 1.0  
    End Sub  
  
    Function GetName() As String  
        Return name  
    End Function          
End Class  
  
' Class with the Author attribute  
<Author("P. Ackerman")>   
Public Class FirstClass  
End Class  
  
' Class without the Author attribute  
Public Class SecondClass  
End Class  
  
' Class with multiple Author attributes.  
<Author("P. Ackerman"), Author("R. Koch", Version:=2.0)>   
Public Class ThirdClass  
End Class  
  
Class TestAuthorAttribute  
    Sub Main()  
        PrintAuthorInfo(GetType(FirstClass))  
        PrintAuthorInfo(GetType(SecondClass))  
        PrintAuthorInfo(GetType(ThirdClass))  
    End Sub  
  
    Private Shared Sub PrintAuthorInfo(ByVal t As System.Type)  
        System.Console.WriteLine("Author information for {0}", t)  
  
        ' Using reflection  
        Dim attrs() As System.Attribute = System.Attribute.GetCustomAttributes(t)  
  
        ' Displaying output  
        For Each attr In attrs  
            Dim a As Author = CType(attr, Author)  
            System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version)  
        Next              
    End Sub  
  
    ' Output:  
    '   Author information for FirstClass  
    '     P. Ackerman, version 1.00  
    ' Author information for SecondClass  
    ' Author information for ThirdClass  
    '  R. Koch, version 2.00  
    '  P. Ackerman, version 1.00  
  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="0459a-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="0459a-118">See Also</span></span>  
 <span data-ttu-id="0459a-119"><xref:System.Reflection></xref:System.Reflection></span><span class="sxs-lookup"><span data-stu-id="0459a-119"><xref:System.Reflection></span></span>   
 <span data-ttu-id="0459a-120"><xref:System.Attribute></xref:System.Attribute></span><span class="sxs-lookup"><span data-stu-id="0459a-120"><xref:System.Attribute></span></span>   
<span data-ttu-id="0459a-121"> [Visual Basic のプログラミング ガイド](../../../../visual-basic/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="0459a-121"> [Visual Basic Programming Guide](../../../../visual-basic/programming-guide/index.md) </span></span>  
<span data-ttu-id="0459a-122"> [属性に格納されている情報を取得します。](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c) </span><span class="sxs-lookup"><span data-stu-id="0459a-122"> [Retrieving Information Stored in Attributes](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c) </span></span>  
<span data-ttu-id="0459a-123"> [リフレクション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="0459a-123"> [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span></span>  
<span data-ttu-id="0459a-124"> [属性 (Visual Basic)](../../../../visual-basic/language-reference/attributes.md) </span><span class="sxs-lookup"><span data-stu-id="0459a-124"> [Attributes (Visual Basic)](../../../../visual-basic/language-reference/attributes.md) </span></span>  
<span data-ttu-id="0459a-125"> [カスタム属性 (Visual Basic) の作成](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)</span><span class="sxs-lookup"><span data-stu-id="0459a-125"> [Creating Custom Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)</span></span>
