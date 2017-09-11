---
title: "&lt;typeparamref&gt; (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- typeparamref
dev_langs:
- CSharp
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
caps.latest.revision: 15
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
ms.openlocfilehash: ce2aba7a14047066decf85675233a48a08bfd605
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="lttypeparamrefgt-c-programming-guide"></a><span data-ttu-id="b786d-102">&lt;typeparamref&gt; (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="b786d-102">&lt;typeparamref&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="b786d-103">構文</span><span class="sxs-lookup"><span data-stu-id="b786d-103">Syntax</span></span>  
  
```xml  
<typeparamref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b786d-104">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b786d-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="b786d-105">型パラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="b786d-105">The name of the type parameter.</span></span> <span data-ttu-id="b786d-106">名前は二重引用符 (" ") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="b786d-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b786d-107">コメント</span><span class="sxs-lookup"><span data-stu-id="b786d-107">Remarks</span></span>  
 <span data-ttu-id="b786d-108">ジェネリック型およびメソッドの型パラメーターの詳細については、「[ジェネリック (C# プログラミング ガイド)](../../../csharp/programming-guide/generics/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b786d-108">For more information on type parameters in generic types and methods, see [Generics](../../../csharp/programming-guide/generics/index.md).</span></span>  
  
 <span data-ttu-id="b786d-109">ドキュメント ファイルを使用するときに何らかの方法で単語の書式 (斜体など) を指定するには、このタグを使用します。</span><span class="sxs-lookup"><span data-stu-id="b786d-109">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>  
  
 <span data-ttu-id="b786d-110">コンパイル時に [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="b786d-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b786d-111">例</span><span class="sxs-lookup"><span data-stu-id="b786d-111">Example</span></span>  
 <span data-ttu-id="b786d-112">[!code-cs[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparamref_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b786d-112">[!code-cs[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparamref_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b786d-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="b786d-113">See Also</span></span>  
 <span data-ttu-id="b786d-114">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b786d-114">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="b786d-115">ドキュメント コメントとして推奨されるタグ</span><span class="sxs-lookup"><span data-stu-id="b786d-115">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

