---
title: リフレクション (Visual Basic) を使用して属性へのアクセス
ms.date: 07/20/2015
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
ms.openlocfilehash: dca476eef392a2f57d0c66727c53e0e53310d679
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a><span data-ttu-id="2035f-102">リフレクション (Visual Basic) を使用して属性へのアクセス</span><span class="sxs-lookup"><span data-stu-id="2035f-102">Accessing Attributes by Using Reflection (Visual Basic)</span></span>
<span data-ttu-id="2035f-103">カスタム属性を定義し、それらをソース コード内に配置することができても、その情報を取得して操作する手段がなければ、ほとんど価値はありません。</span><span class="sxs-lookup"><span data-stu-id="2035f-103">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="2035f-104">リフレクションを使用すれば、カスタム属性を使用して定義された情報を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="2035f-104">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="2035f-105">鍵となるメソッドは `GetCustomAttributes` です。このメソッドは、ソース コード属性の実行時の等価オブジェクトを配列で返します。</span><span class="sxs-lookup"><span data-stu-id="2035f-105">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="2035f-106">このメソッドには、いくつかのオーバー ロード バージョンがあります。</span><span class="sxs-lookup"><span data-stu-id="2035f-106">This method has several overloaded versions.</span></span> <span data-ttu-id="2035f-107">詳細については、「<xref:System.Attribute>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2035f-107">For more information, see <xref:System.Attribute>.</span></span>  
  
 <span data-ttu-id="2035f-108">次のような属性指定は、</span><span class="sxs-lookup"><span data-stu-id="2035f-108">An attribute specification such as:</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 <span data-ttu-id="2035f-109">概念的には次の記述と同じです。</span><span class="sxs-lookup"><span data-stu-id="2035f-109">is conceptually equivalent to this:</span></span>  
  
```vb  
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")  
anonymousAuthorObject.version = 1.1  
```  
  
 <span data-ttu-id="2035f-110">ただし、属性について `SampleClass` が照会されるまで、コードは実行されません。</span><span class="sxs-lookup"><span data-stu-id="2035f-110">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="2035f-111">`SampleClass` について `GetCustomAttributes` を呼び出すと、`Author` オブジェクトが作成され、上記のように初期化されます。</span><span class="sxs-lookup"><span data-stu-id="2035f-111">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="2035f-112">クラスに他の属性がある場合は、他の属性オブジェクトも同様に作成されます。</span><span class="sxs-lookup"><span data-stu-id="2035f-112">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="2035f-113">`GetCustomAttributes` はその後、`Author` オブジェクトと配列内の他の属性オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="2035f-113">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="2035f-114">その後、この配列を反復処理し、各配列要素の型に基づいてどの属性が適用されたかを確認して、属性オブジェクトから情報を抽出することができます。</span><span class="sxs-lookup"><span data-stu-id="2035f-114">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2035f-115">例</span><span class="sxs-lookup"><span data-stu-id="2035f-115">Example</span></span>  
 <span data-ttu-id="2035f-116">完全な例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="2035f-116">Here is a complete example.</span></span> <span data-ttu-id="2035f-117">カスタム属性が定義され、複数のエンティティに適用された後、リフレクションを使用して取得されています。</span><span class="sxs-lookup"><span data-stu-id="2035f-117">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2035f-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="2035f-118">See Also</span></span>  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [<span data-ttu-id="2035f-119">Visual Basic プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="2035f-119">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="2035f-120">属性に格納されている情報の取得</span><span class="sxs-lookup"><span data-stu-id="2035f-120">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
 [<span data-ttu-id="2035f-121">リフレクション (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2035f-121">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="2035f-122">属性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2035f-122">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)  
 [<span data-ttu-id="2035f-123">カスタム属性の作成 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2035f-123">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
