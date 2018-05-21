---
title: '&lt;typeparamref&gt; (C# プログラミング ガイド)'
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 36e5a8998018839214da00287a2bf8dc2c5925a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="lttypeparamrefgt-c-programming-guide"></a><span data-ttu-id="e38ed-102">&lt;typeparamref&gt; (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="e38ed-102">&lt;typeparamref&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="e38ed-103">構文</span><span class="sxs-lookup"><span data-stu-id="e38ed-103">Syntax</span></span>  
  
```xml  
<typeparamref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e38ed-104">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e38ed-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="e38ed-105">型パラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="e38ed-105">The name of the type parameter.</span></span> <span data-ttu-id="e38ed-106">名前は二重引用符 (" ") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="e38ed-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e38ed-107">コメント</span><span class="sxs-lookup"><span data-stu-id="e38ed-107">Remarks</span></span>  
 <span data-ttu-id="e38ed-108">ジェネリック型およびメソッドの型パラメーターの詳細については、「[ジェネリック (C# プログラミング ガイド)](../../../csharp/programming-guide/generics/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e38ed-108">For more information on type parameters in generic types and methods, see [Generics](../../../csharp/programming-guide/generics/index.md).</span></span>  
  
 <span data-ttu-id="e38ed-109">ドキュメント ファイルを使用するときに何らかの方法で単語の書式 (斜体など) を指定するには、このタグを使用します。</span><span class="sxs-lookup"><span data-stu-id="e38ed-109">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>  
  
 <span data-ttu-id="e38ed-110">コンパイル時に [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="e38ed-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e38ed-111">例</span><span class="sxs-lookup"><span data-stu-id="e38ed-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparamref_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e38ed-112">参照</span><span class="sxs-lookup"><span data-stu-id="e38ed-112">See Also</span></span>  
 [<span data-ttu-id="e38ed-113">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="e38ed-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e38ed-114">ドキュメント コメントとして推奨されるタグ</span><span class="sxs-lookup"><span data-stu-id="e38ed-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
