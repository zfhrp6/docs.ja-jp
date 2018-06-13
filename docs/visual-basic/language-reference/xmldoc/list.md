---
title: '&lt;リスト&gt;(Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- listheader XML tag
- <item> XML tag
- <list> XML tag
- <listheader> XML tag
- term XML tag
- list XML tag
- <description> XML tag
- description XML tag
- item XML tag
- <term> XML tag
ms.assetid: ec35fced-d58e-4520-a764-0691256e014b
ms.openlocfilehash: f03924217393e1e909b086b282f1c62ddb471522
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603614"
---
# <a name="ltlistgt-visual-basic"></a><span data-ttu-id="d911b-102">&lt;リスト&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d911b-102">&lt;list&gt; (Visual Basic)</span></span>
<span data-ttu-id="d911b-103">リストまたはテーブルを定義します。</span><span class="sxs-lookup"><span data-stu-id="d911b-103">Defines a list or table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d911b-104">構文</span><span class="sxs-lookup"><span data-stu-id="d911b-104">Syntax</span></span>  
  
```xml  
<list type="type">  
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
  
#### <a name="parameters"></a><span data-ttu-id="d911b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d911b-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="d911b-106">リストの型。</span><span class="sxs-lookup"><span data-stu-id="d911b-106">The type of the list.</span></span> <span data-ttu-id="d911b-107">箇条書きリスト、番号付きリストは、または 2 つの列のテーブルには、"table"の"number"の「行頭文字」をする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d911b-107">Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.</span></span>  
  
 `term`  
 <span data-ttu-id="d911b-108">場合のみ使用`type`"table"には</span><span class="sxs-lookup"><span data-stu-id="d911b-108">Only used when `type` is "table."</span></span> <span data-ttu-id="d911b-109">説明タグで定義されている用語を定義します。</span><span class="sxs-lookup"><span data-stu-id="d911b-109">A term to define, which is defined in the description tag.</span></span>  
  
 `description`  
 <span data-ttu-id="d911b-110">ときに`type`「の行頭文字」または「番号」 `description` 、リスト内の項目は、ときに`type`"table"は`description`の定義は、`term`です。</span><span class="sxs-lookup"><span data-stu-id="d911b-110">When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d911b-111">コメント</span><span class="sxs-lookup"><span data-stu-id="d911b-111">Remarks</span></span>  
 <span data-ttu-id="d911b-112">`<listheader>`ブロックは、テーブルまたは定義の一覧の見出しを定義します。</span><span class="sxs-lookup"><span data-stu-id="d911b-112">The `<listheader>` block defines the heading of either a table or definition list.</span></span> <span data-ttu-id="d911b-113">のみのエントリを指定する必要があるテーブルを定義するときに`term`見出しにします。</span><span class="sxs-lookup"><span data-stu-id="d911b-113">When defining a table, you only have to supply an entry for `term` in the heading.</span></span>  
  
 <span data-ttu-id="d911b-114">リスト内の各項目を指定した、`<item>`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="d911b-114">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="d911b-115">定義リストを作成するときに、両方を指定する必要があります`term`と`description`です。</span><span class="sxs-lookup"><span data-stu-id="d911b-115">When creating a definition list, you must specify both `term` and `description`.</span></span> <span data-ttu-id="d911b-116">ただし、テーブル、箇条書きリスト、または番号付きリストにのみ指定する必要のエントリ`description`です。</span><span class="sxs-lookup"><span data-stu-id="d911b-116">However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="d911b-117">リストまたはテーブルに指定できるは多く`<item>`に応じてをブロックします。</span><span class="sxs-lookup"><span data-stu-id="d911b-117">A list or table can have as many `<item>` blocks as needed.</span></span>  
  
 <span data-ttu-id="d911b-118">コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="d911b-118">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d911b-119">例</span><span class="sxs-lookup"><span data-stu-id="d911b-119">Example</span></span>  
 <span data-ttu-id="d911b-120">この例では、 `<list>` 「解説」セクションで、箇条書きリストを定義するタグです。</span><span class="sxs-lookup"><span data-stu-id="d911b-120">This example uses the `<list>` tag to define a bulleted list in the remarks section.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#5](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/list_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d911b-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="d911b-121">See Also</span></span>  
 [<span data-ttu-id="d911b-122">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="d911b-122">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
