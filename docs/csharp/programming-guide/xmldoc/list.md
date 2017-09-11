---
title: "&lt;list&gt; (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- list
- <list>
dev_langs:
- CSharp
helpviewer_keywords:
- list C# XML tag
- listheader C# XML tag
- <listheader> C# XML tag
- item C# XML tag
- <item> C# XML tag
- <list> C# XML tag
ms.assetid: c9620b1b-c2e6-43f1-ab88-8ab47308ffec
caps.latest.revision: 11
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
ms.openlocfilehash: b9d3dfa60530734a142295c8a8f2c32c4ecd9a47
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="ltlistgt-c-programming-guide"></a><span data-ttu-id="ea85e-102">&lt;list&gt; (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="ea85e-102">&lt;list&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="ea85e-103">構文</span><span class="sxs-lookup"><span data-stu-id="ea85e-103">Syntax</span></span>  
  
```xml  
<list type="bullet" | "number" | "table">  
    <listheader>  
        <term>term</term>  
        <description>description</description>  
    </listheader>  
    <item>  
        <term>term</term>  
        <description>description</description>  
    </item>  
</list>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ea85e-104">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ea85e-104">Parameters</span></span>  
 `term`  
 <span data-ttu-id="ea85e-105">定義される用語であり、`description` で定義されます。</span><span class="sxs-lookup"><span data-stu-id="ea85e-105">A term to define, which will be defined in `description`.</span></span>  
  
 `description`  
 <span data-ttu-id="ea85e-106">行頭文字または番号付きリストの項目、または `term` の定義です。</span><span class="sxs-lookup"><span data-stu-id="ea85e-106">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea85e-107">コメント</span><span class="sxs-lookup"><span data-stu-id="ea85e-107">Remarks</span></span>  
 <span data-ttu-id="ea85e-108">\< > ブロックを使用して、テーブルまたは定義の一覧の見出し行を定義します。</span><span class="sxs-lookup"><span data-stu-id="ea85e-108">The \<listheader> block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="ea85e-109">テーブルを定義するときにのみ、見出しの用語のエントリを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea85e-109">When defining a table, you only need to supply an entry for term in the heading.</span></span>  
  
 <span data-ttu-id="ea85e-110">リスト内の各項目は、\<item> ブロックで指定されます。</span><span class="sxs-lookup"><span data-stu-id="ea85e-110">Each item in the list is specified with an \<item> block.</span></span> <span data-ttu-id="ea85e-111">定義リストを作成する場合は、`term` と `description` の両方を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea85e-111">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="ea85e-112">ただし、テーブル、箇条書きリスト、または番号付きリストの場合は、`description` のエントリを指定するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="ea85e-112">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="ea85e-113">リストまたはテーブルでは、必要な数の \<item> ブロックを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ea85e-113">A list or table can have as many \<item> blocks as needed.</span></span>  
  
 <span data-ttu-id="ea85e-114">コンパイル時に [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="ea85e-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea85e-115">例</span><span class="sxs-lookup"><span data-stu-id="ea85e-115">Example</span></span>  
 <span data-ttu-id="ea85e-116">[!code-cs[csProgGuideDocComments#6](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/list_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ea85e-116">[!code-cs[csProgGuideDocComments#6](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/list_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea85e-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea85e-117">See Also</span></span>  
 <span data-ttu-id="ea85e-118">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ea85e-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="ea85e-119">ドキュメント コメントとして推奨されるタグ</span><span class="sxs-lookup"><span data-stu-id="ea85e-119">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

