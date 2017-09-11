---
title: "カスタム属性 (Visual Basic) の作成 |Microsoft ドキュメント"
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
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
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
ms.openlocfilehash: fbfc3f84f6287d233d475f01869dab63b937a521
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="creating-custom-attributes-visual-basic"></a><span data-ttu-id="56b41-102">カスタム属性 (Visual Basic) の作成</span><span class="sxs-lookup"><span data-stu-id="56b41-102">Creating Custom Attributes (Visual Basic)</span></span>
<span data-ttu-id="56b41-103">独自のカスタム属性を作成するには、属性クラスから直接または間接的に派生したクラスを定義することで<xref:System.Attribute>、迅速かつ容易なメタデータで属性の定義を識別するため、</xref:System.Attribute> 。</span><span class="sxs-lookup"><span data-stu-id="56b41-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="56b41-104">タグという名前の型の型を記述したプログラマにするとします。</span><span class="sxs-lookup"><span data-stu-id="56b41-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="56b41-105">カスタムを定義することも`Author`属性クラス。</span><span class="sxs-lookup"><span data-stu-id="56b41-105">You might define a custom `Author` attribute class:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct)>   
Public Class Author  
    Inherits System.Attribute  
    Private name As String  
    Public version As Double  
    Sub New(ByVal authorName As String)  
        name = authorName  
        version = 1.0  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="56b41-106">クラス名は、属性の名`Author`します。</span><span class="sxs-lookup"><span data-stu-id="56b41-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="56b41-107">派生`System.Attribute`ので、これはカスタム属性クラスです。</span><span class="sxs-lookup"><span data-stu-id="56b41-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="56b41-108">コンス トラクターのパラメーターは、カスタム属性の位置指定パラメーターです。</span><span class="sxs-lookup"><span data-stu-id="56b41-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="56b41-109">この例では`name`位置指定パラメーターです。</span><span class="sxs-lookup"><span data-stu-id="56b41-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="56b41-110">任意の読み取り/書き込みのパブリック フィールドまたはプロパティは名前付きパラメーター。</span><span class="sxs-lookup"><span data-stu-id="56b41-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="56b41-111">この場合、`version`はのみ名前付きパラメーター。</span><span class="sxs-lookup"><span data-stu-id="56b41-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="56b41-112">使用に注意してください、`AttributeUsage`属性を`Author`属性がクラスでのみ有効と`Structure`宣言します。</span><span class="sxs-lookup"><span data-stu-id="56b41-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `Structure` declarations.</span></span>  
  
 <span data-ttu-id="56b41-113">次のように、この新しい属性を使用できます。</span><span class="sxs-lookup"><span data-stu-id="56b41-113">You could use this new attribute as follows:</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
End Class  
```  
  
 <span data-ttu-id="56b41-114">`AttributeUsage`名前付きパラメーターを持つ`AllowMultiple`、これは、カスタム属性単一目的または multiuse とします。</span><span class="sxs-lookup"><span data-stu-id="56b41-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="56b41-115">次のコード例では、multiuse 属性が作成されます。</span><span class="sxs-lookup"><span data-stu-id="56b41-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```vb  
' multiuse attribute  
<System.AttributeUsage(System.AttributeTargets.Class Or   
                       System.AttributeTargets.Struct,   
                       AllowMultiple:=True)>   
Public Class Author  
    Inherits System.Attribute  
```  
  
 <span data-ttu-id="56b41-116">次のコード例では、同じ種類の複数の属性がクラスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="56b41-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```vb  
<Author("P. Ackerman", Version:=1.1),   
Author("R. Koch", Version:=1.2)>   
Class SampleClass  
    ' P. Ackerman's code goes here...  
    ' R. Koch's code goes here...  
End Class  
```  
  
> [!NOTE]
>  <span data-ttu-id="56b41-117">属性クラスにプロパティが含まれている場合、そのプロパティは読み取り/書き込みをする必要があります。</span><span class="sxs-lookup"><span data-stu-id="56b41-117">If your attribute class contains a property, that property must be read-write.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56b41-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="56b41-118">See Also</span></span>  
 <span data-ttu-id="56b41-119"><xref:System.Reflection></xref:System.Reflection></span><span class="sxs-lookup"><span data-stu-id="56b41-119"><xref:System.Reflection></span></span>   
<span data-ttu-id="56b41-120"> [Visual Basic のプログラミング ガイド](../../../../visual-basic/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="56b41-120"> [Visual Basic Programming Guide](../../../../visual-basic/programming-guide/index.md) </span></span>  
<span data-ttu-id="56b41-121"> [カスタム属性の記述](http://msdn.microsoft.com/library/97216f69-bde8-49fd-ac40-f18c500ef5dc) </span><span class="sxs-lookup"><span data-stu-id="56b41-121"> [Writing Custom Attributes](http://msdn.microsoft.com/library/97216f69-bde8-49fd-ac40-f18c500ef5dc) </span></span>  
<span data-ttu-id="56b41-122"> [リフレクション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="56b41-122"> [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span></span>  
<span data-ttu-id="56b41-123"> [属性 (Visual Basic)](../../../../visual-basic/language-reference/attributes.md) </span><span class="sxs-lookup"><span data-stu-id="56b41-123"> [Attributes (Visual Basic)](../../../../visual-basic/language-reference/attributes.md) </span></span>  
<span data-ttu-id="56b41-124"> [リフレクション (Visual Basic) を使用して属性へのアクセス](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md) </span><span class="sxs-lookup"><span data-stu-id="56b41-124"> [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md) </span></span>  
<span data-ttu-id="56b41-125"> [AttributeUsage (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)</span><span class="sxs-lookup"><span data-stu-id="56b41-125"> [AttributeUsage (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)</span></span>
