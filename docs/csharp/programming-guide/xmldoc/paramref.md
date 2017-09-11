---
title: "&lt;paramref&gt; (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- paramref
- <paramref>
dev_langs:
- CSharp
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
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
ms.openlocfilehash: 452701c4f70bf6cbc619064d62de552fa54bba65
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="ltparamrefgt-c-programming-guide"></a><span data-ttu-id="4bd6d-102">&lt;paramref&gt; (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="4bd6d-102">&lt;paramref&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="4bd6d-103">構文</span><span class="sxs-lookup"><span data-stu-id="4bd6d-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4bd6d-104">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4bd6d-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="4bd6d-105">参照されるパラメーターの名前です。</span><span class="sxs-lookup"><span data-stu-id="4bd6d-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="4bd6d-106">名前は二重引用符 (" ") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="4bd6d-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4bd6d-107">コメント</span><span class="sxs-lookup"><span data-stu-id="4bd6d-107">Remarks</span></span>  
 <span data-ttu-id="4bd6d-108">\<paramref> タグを使用すると、\<summary> または \<remarks> ブロックなどのコード コメント内の単語がパラメーターを参照することを示すことができます。</span><span class="sxs-lookup"><span data-stu-id="4bd6d-108">The \<paramref> tag gives you a way to indicate that a word in the code comments, for example in a \<summary> or \<remarks> block refers to a parameter.</span></span> <span data-ttu-id="4bd6d-109">この単語を、太字や斜体のフォントを使うなど、何らかの独自の方法で書式設定するために XML ファイルを処理できます。</span><span class="sxs-lookup"><span data-stu-id="4bd6d-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>  
  
 <span data-ttu-id="4bd6d-110">コンパイル時に [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="4bd6d-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bd6d-111">例</span><span class="sxs-lookup"><span data-stu-id="4bd6d-111">Example</span></span>  
 <span data-ttu-id="4bd6d-112">[!code-cs[csProgGuideDocComments#7](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/paramref_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="4bd6d-112">[!code-cs[csProgGuideDocComments#7](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/paramref_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bd6d-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="4bd6d-113">See Also</span></span>  
 <span data-ttu-id="4bd6d-114">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="4bd6d-114">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="4bd6d-115">ドキュメント コメントとして推奨されるタグ</span><span class="sxs-lookup"><span data-stu-id="4bd6d-115">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

