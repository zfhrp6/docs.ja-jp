---
title: "&lt;c&gt; (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- c
- <c>
dev_langs:
- CSharp
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
caps.latest.revision: 12
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
ms.openlocfilehash: 5a06e25061d4b98ee5e299089455224d39363a63
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="ltcgt-c-programming-guide"></a><span data-ttu-id="83f2e-102">&lt;c&gt; (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="83f2e-102">&lt;c&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="83f2e-103">構文</span><span class="sxs-lookup"><span data-stu-id="83f2e-103">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83f2e-104">パラメーター</span><span class="sxs-lookup"><span data-stu-id="83f2e-104">Parameters</span></span>  
 `text`  
 <span data-ttu-id="83f2e-105">コードとして指定するテキストです。</span><span class="sxs-lookup"><span data-stu-id="83f2e-105">The text you would like to indicate as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83f2e-106">コメント</span><span class="sxs-lookup"><span data-stu-id="83f2e-106">Remarks</span></span>  
 <span data-ttu-id="83f2e-107">\<c> タグを使用すると、説明内のテキストをコードとして指定できます。</span><span class="sxs-lookup"><span data-stu-id="83f2e-107">The \<c> tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="83f2e-108">複数行をコードとして指定する場合は、[\<code>](../../../csharp/programming-guide/xmldoc/code.md) タグを使用します。</span><span class="sxs-lookup"><span data-stu-id="83f2e-108">Use [\<code>](../../../csharp/programming-guide/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="83f2e-109">コンパイル時に [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定してドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="83f2e-109">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83f2e-110">例</span><span class="sxs-lookup"><span data-stu-id="83f2e-110">Example</span></span>  
 <span data-ttu-id="83f2e-111">[!code-cs[csProgGuideDocComments#2](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/code-inline_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="83f2e-111">[!code-cs[csProgGuideDocComments#2](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/code-inline_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83f2e-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="83f2e-112">See Also</span></span>  
 <span data-ttu-id="83f2e-113">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="83f2e-113">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="83f2e-114">ドキュメント コメントとして推奨されるタグ</span><span class="sxs-lookup"><span data-stu-id="83f2e-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

