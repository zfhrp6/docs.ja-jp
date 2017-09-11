---
title: "&lt;summary&gt; (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <summary>
- summary
dev_langs:
- CSharp
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: bd96e58494196fcfdeb46e9e59481666ec9466f3
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="ltsummarygt-c-programming-guide"></a><span data-ttu-id="aad8c-102">&lt;summary&gt; (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="aad8c-102">&lt;summary&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="aad8c-103">構文</span><span class="sxs-lookup"><span data-stu-id="aad8c-103">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aad8c-104">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aad8c-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="aad8c-105">オブジェクトの概要。</span><span class="sxs-lookup"><span data-stu-id="aad8c-105">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aad8c-106">コメント</span><span class="sxs-lookup"><span data-stu-id="aad8c-106">Remarks</span></span>  
 <span data-ttu-id="aad8c-107">\<summary> タグは、型または型のメンバーの説明に使用します。</span><span class="sxs-lookup"><span data-stu-id="aad8c-107">The \<summary> tag should be used to describe a type or a type member.</span></span> <span data-ttu-id="aad8c-108">型の説明に補足情報を追加するには、[\<remarks>](../../../csharp/programming-guide/xmldoc/remarks.md) タグを使用します。</span><span class="sxs-lookup"><span data-stu-id="aad8c-108">Use [\<remarks>](../../../csharp/programming-guide/xmldoc/remarks.md) to add supplemental information to a type description.</span></span> <span data-ttu-id="aad8c-109">[Sandcastle](https://github.com/EWSoftware/SHFB) などのドキュメント ツールでコード要素のドキュメント ページへの内部ハイパーリンクを作成できるようにするには、[cref 属性](../../../csharp/programming-guide/xmldoc/cref-attribute.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="aad8c-109">Use the [cref Attribute](../../../csharp/programming-guide/xmldoc/cref-attribute.md) to enable documentation tools such as [Sandcastle](https://github.com/EWSoftware/SHFB) to create internal hyperlinks to documentation pages for code elements.</span></span>  
  
 <span data-ttu-id="aad8c-110">\<summary> タグのテキストは、IntelliSense の型に関する唯一のソースで、オブジェクト ブラウザー ウィンドウにも表示されます。</span><span class="sxs-lookup"><span data-stu-id="aad8c-110">The text for the \<summary> tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser Window.</span></span>  
  
 <span data-ttu-id="aad8c-111">コンパイル時に [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="aad8c-111">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span> <span data-ttu-id="aad8c-112">コンパイラによって生成されたファイルに基づいて最終的なドキュメントを作成するには、カスタム ツールを作成するか、[Sandcastle](https://github.com/EWSoftware/SHFB) などのツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="aad8c-112">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aad8c-113">例</span><span class="sxs-lookup"><span data-stu-id="aad8c-113">Example</span></span>  
 <span data-ttu-id="aad8c-114">[!code-cs[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/summary_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="aad8c-114">[!code-cs[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/summary_1.cs)]</span></span>  
  
 <span data-ttu-id="aad8c-115">前の例では、次の XML ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="aad8c-115">The previous example produces the following XML file.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>YourNamespace</name>  
    </assembly>  
    <members>  
        <member name="T:DotNetEvents.TestClass">  
            text for class TestClass  
        </member>  
        <member name="M:DotNetEvents.TestClass.DoWork(System.Int32)">  
            <summary>DoWork is a method in the TestClass class.  
            <para>Here's how you could make a second paragraph in a description. <see cref="M:System.Console.WriteLine(System.String)"/> for information about output statements.</para>  
            <seealso cref="M:DotNetEvents.TestClass.Main"/>  
            </summary>  
        </member>  
        <member name="M:DotNetEvents.TestClass.Main">  
            text for Main  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="example"></a><span data-ttu-id="aad8c-116">例</span><span class="sxs-lookup"><span data-stu-id="aad8c-116">Example</span></span>  
 <span data-ttu-id="aad8c-117">ジェネリック型への `cref` 参照を作成する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="aad8c-117">The following example shows how to make a `cref` reference to a generic type.</span></span>  
  
 <span data-ttu-id="aad8c-118">[!code-cs[csProgGuideDocComments#11](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/summary_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="aad8c-118">[!code-cs[csProgGuideDocComments#11](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/summary_2.cs)]</span></span>  
  
 <span data-ttu-id="aad8c-119">前の例では、次の XML ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="aad8c-119">The previous example produces the following XML file.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>YourNamespace</name>  
    </assembly>  
    <members>  
        <member name="T:ExtensionMethodsDemo1.A">  
            <summary cref="T:ExtensionMethodsDemo1.C`1">  
            </summary>  
        </member>  
        <member name="T:ExtensionMethodsDemo1.B">  
            <summary cref="T:C`1">  
            </summary>  
        </member>  
        <member name="T:ExtensionMethodsDemo1.C`1">  
            <summary cref="T:ExtensionMethodsDemo1.A">  
            </summary>  
            <typeparam name="T"></typeparam>  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aad8c-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="aad8c-120">See Also</span></span>  
 <span data-ttu-id="aad8c-121">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="aad8c-121">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="aad8c-122">ドキュメント コメントとして推奨されるタグ</span><span class="sxs-lookup"><span data-stu-id="aad8c-122">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

