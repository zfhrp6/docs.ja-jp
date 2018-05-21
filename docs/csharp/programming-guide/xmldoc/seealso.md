---
title: '&lt;seealso&gt; (C# プログラミング ガイド)'
ms.date: 07/20/2015
f1_keywords:
- cref
- <seealso>
- seealso
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
ms.openlocfilehash: e3c9d68884e5cd4f5a4f81580f60cdde775458a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ltseealsogt-c-programming-guide"></a><span data-ttu-id="4bb39-102">&lt;seealso&gt; (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="4bb39-102">&lt;seealso&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="4bb39-103">構文</span><span class="sxs-lookup"><span data-stu-id="4bb39-103">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4bb39-104">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4bb39-104">Parameters</span></span>  
 <span data-ttu-id="4bb39-105">cref = "`member`"</span><span class="sxs-lookup"><span data-stu-id="4bb39-105">cref = " `member`"</span></span>  
 <span data-ttu-id="4bb39-106">現在のコンパイル環境からの呼び出しに利用できる、メンバーまたはフィールドへの参照。</span><span class="sxs-lookup"><span data-stu-id="4bb39-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="4bb39-107">コンパイラは、指定されたコード要素が存在するかどうかを確認し、`member` を出力 XML 内の要素名に渡します。`member`</span><span class="sxs-lookup"><span data-stu-id="4bb39-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="4bb39-108">は二重引用符 (" ") で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bb39-108">must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="4bb39-109">ジェネリック型への cref 参照を作成する方法については、「[\<see>](../../../csharp/programming-guide/xmldoc/see.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bb39-109">For information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4bb39-110">コメント</span><span class="sxs-lookup"><span data-stu-id="4bb39-110">Remarks</span></span>  
 <span data-ttu-id="4bb39-111">\<seealso > タグを使用して、「See Also」セクションに表示するテキストを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="4bb39-111">The \<seealso> tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="4bb39-112">[\<see>](../../../csharp/programming-guide/xmldoc/see.md) タグを使用すると、テキスト内からリンクを指定できます。</span><span class="sxs-lookup"><span data-stu-id="4bb39-112">Use [\<see>](../../../csharp/programming-guide/xmldoc/see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="4bb39-113">コンパイル時に [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="4bb39-113">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bb39-114">例</span><span class="sxs-lookup"><span data-stu-id="4bb39-114">Example</span></span>  
 <span data-ttu-id="4bb39-115">\<seealso> の使用例については、[\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bb39-115">See [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) for an example of using \<seealso>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bb39-116">参照</span><span class="sxs-lookup"><span data-stu-id="4bb39-116">See Also</span></span>  
 [<span data-ttu-id="4bb39-117">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="4bb39-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4bb39-118">ドキュメント コメントとして推奨されるタグ</span><span class="sxs-lookup"><span data-stu-id="4bb39-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
