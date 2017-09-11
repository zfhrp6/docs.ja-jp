---
title: "cref 属性 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- cref [C#]
ms.assetid: 66a6b0e5-b961-4504-a461-3a4cf481fc8b
caps.latest.revision: 10
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7861d6696b7a40b8a665d489b92a3b196a7dd0ce
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="cref-attribute-c-programming-guide"></a><span data-ttu-id="244c3-102">cref 属性 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="244c3-102">cref Attribute (C# Programming Guide)</span></span>
<span data-ttu-id="244c3-103">XML ドキュメント タグの `cref` 属性は "コード参照" を意味します。</span><span class="sxs-lookup"><span data-stu-id="244c3-103">The `cref` attribute in an XML documentation tag means "code reference."</span></span> <span data-ttu-id="244c3-104">タグの内部テキストが、型、メソッド、プロパティなど、コード要素であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="244c3-104">It specifies that the inner text of the tag is a code element, such as a type, method, or property.</span></span> <span data-ttu-id="244c3-105">[Sandcastle](https://github.com/EWSoftware/SHFB) のようなドキュメント ツールは `cref` 属性を利用し、型やメンバーが文書化されるページのハイパーリンクを自動的に生成します。</span><span class="sxs-lookup"><span data-stu-id="244c3-105">Documentation tools like [Sandcastle](https://github.com/EWSoftware/SHFB) use the `cref` attributes to automatically generate hyperlinks to the page where the type or member is documented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="244c3-106">例</span><span class="sxs-lookup"><span data-stu-id="244c3-106">Example</span></span>  
 <span data-ttu-id="244c3-107">次の例は、[\<see>](../../../csharp/programming-guide/xmldoc/see.md) タグで使用される `cref` 属性のものです。</span><span class="sxs-lookup"><span data-stu-id="244c3-107">The following example shows `cref` attributes used in [\<see>](../../../csharp/programming-guide/xmldoc/see.md) tags.</span></span>  
  
 <span data-ttu-id="244c3-108">[!code-cs[csProgGuideDocComments#3](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/cref-attribute_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="244c3-108">[!code-cs[csProgGuideDocComments#3](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/cref-attribute_1.cs)]</span></span>  
  
 <span data-ttu-id="244c3-109">コンパイルすると、このプログラムの XML 出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="244c3-109">When compiled, the program produces the following XML file.</span></span> <span data-ttu-id="244c3-110">たとえば、`GetZero` メソッドの `cref` 属性がコンパイラにより `"M:TestNamespace.TestClass.GetZero"` に変換されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="244c3-110">Notice that the `cref` attribute for the `GetZero` method, for example, has been transformed by the compiler to `"M:TestNamespace.TestClass.GetZero"`.</span></span> <span data-ttu-id="244c3-111">"M:" プレフィックスは "method" という意味であり、Sandcastle のようなドキュメント ツールで認識される規約です。</span><span class="sxs-lookup"><span data-stu-id="244c3-111">The "M:" prefix means "method" and is a convention that is recognized by documentation tools such as Sandcastle.</span></span> <span data-ttu-id="244c3-112">プレフィックスの完全一覧については、「[XML ファイルの処理](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="244c3-112">For a complete list of prefixes, see [Processing the XML File](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md).</span></span>  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>CRefTest</name>  
    </assembly>  
    <members>  
        <member name="T:TestNamespace.TestClass">  
            <summary>  
            TestClass contains cref examples.  
            </summary>  
        </member>  
        <member name="M:TestNamespace.TestClass.#ctor">  
            <summary>  
            This sample shows how to specify the <see cref="T:TestNamespace.TestClass"/> constructor as a cref attribute.   
            </summary>  
        </member>  
        <member name="M:TestNamespace.TestClass.#ctor(System.Int32)">  
            <summary>  
            This sample shows how to specify the <see cref="M:TestNamespace.TestClass.#ctor(System.Int32)"/> constructor as a cref attribute.   
            </summary>  
        </member>  
        <member name="M:TestNamespace.TestClass.GetZero">  
            <summary>  
            The GetZero method.  
            </summary>  
            <example>   
            This sample shows how to call the <see cref="M:TestNamespace.TestClass.GetZero"/> method.  
            <code>  
            class TestClass   
            {  
                static int Main()   
                {  
                    return GetZero();  
                }  
            }  
            </code>  
            </example>  
        </member>  
        <member name="M:TestNamespace.TestClass.GetGenericValue``1(``0)">  
            <summary>  
            The GetGenericValue method.  
            </summary>  
            <remarks>   
            This sample shows how to specify the <see cref="M:TestNamespace.TestClass.GetGenericValue``1(``0)"/> method as a cref attribute.  
            </remarks>  
        </member>  
        <member name="T:TestNamespace.GenericClass`1">  
            <summary>  
            GenericClass.  
            </summary>  
            <remarks>   
            This example shows how to specify the <see cref="T:TestNamespace.GenericClass`1"/> type as a cref attribute.  
            </remarks>  
        </member>  
    </members>    <members>  
        <member name="T:TestNamespace.TestClass">  
            <summary>  
            TestClass contains two cref examples.  
            </summary>  
        </member>  
        <member name="M:TestNamespace.TestClass.GetZero">  
            <summary>  
            The GetZero method.  
            </summary>  
            <example> This sample shows how to call the <see cref="M:TestNamespace.TestClass.GetZero"/> method.  
            <code>  
            class TestClass   
            {  
                static int Main()   
                {  
                    return GetZero();  
                }  
            }  
            </code>  
            </example>  
        </member>  
        <member name="M:TestNamespace.TestClass.GetGenericValue``1(``0)">  
            <summary>  
            The GetGenericValue method.  
            </summary>  
            <remarks>   
            This sample shows how to specify the <see cref="M:TestNamespace.TestClass.GetGenericValue``1(``0)"/> method as a cref attribute.  
            </remarks>  
        </member>  
        <member name="T:TestNamespace.GenericClass`1">  
            <summary>  
            GenericClass.  
            </summary>  
            <remarks>   
            This example shows how to specify the <see cref="T:TestNamespace.GenericClass`1"/> type as a cref attribute.  
            </remarks>  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="see-also"></a><span data-ttu-id="244c3-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="244c3-113">See Also</span></span>  
 <span data-ttu-id="244c3-114">[XML ドキュメント コメント](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md) </span><span class="sxs-lookup"><span data-stu-id="244c3-114">[XML Documentation Comments](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md) </span></span>  
 [<span data-ttu-id="244c3-115">ドキュメント コメントとして推奨されるタグ</span><span class="sxs-lookup"><span data-stu-id="244c3-115">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

