---
title: "&lt;リスト&gt;(Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 34347df88f1bc3097db0020526ec99943c8f7bd4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltlistgt-visual-basic"></a><span data-ttu-id="19325-102">&lt;リスト&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19325-102">&lt;list&gt; (Visual Basic)</span></span>
<span data-ttu-id="19325-103">リストまたはテーブルを定義します。</span><span class="sxs-lookup"><span data-stu-id="19325-103">Defines a list or table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19325-104">構文</span><span class="sxs-lookup"><span data-stu-id="19325-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="19325-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="19325-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="19325-106">リストの型。</span><span class="sxs-lookup"><span data-stu-id="19325-106">The type of the list.</span></span> <span data-ttu-id="19325-107">箇条書きリスト、番号付きリストは、または 2 つの列のテーブルには、"table"の"number"の「行頭文字」をする必要があります。</span><span class="sxs-lookup"><span data-stu-id="19325-107">Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.</span></span>  
  
 `term`  
 <span data-ttu-id="19325-108">場合のみ使用`type`"table"には</span><span class="sxs-lookup"><span data-stu-id="19325-108">Only used when `type` is "table."</span></span> <span data-ttu-id="19325-109">説明タグで定義されている用語を定義します。</span><span class="sxs-lookup"><span data-stu-id="19325-109">A term to define, which is defined in the description tag.</span></span>  
  
 `description`  
 <span data-ttu-id="19325-110">ときに`type`「の行頭文字」または「番号」 `description` 、リスト内の項目は、ときに`type`"table"は`description`の定義は、`term`です。</span><span class="sxs-lookup"><span data-stu-id="19325-110">When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19325-111">コメント</span><span class="sxs-lookup"><span data-stu-id="19325-111">Remarks</span></span>  
 <span data-ttu-id="19325-112">`<listheader>`ブロックは、テーブルまたは定義の一覧の見出しを定義します。</span><span class="sxs-lookup"><span data-stu-id="19325-112">The `<listheader>` block defines the heading of either a table or definition list.</span></span> <span data-ttu-id="19325-113">のみのエントリを指定する必要があるテーブルを定義するときに`term`見出しにします。</span><span class="sxs-lookup"><span data-stu-id="19325-113">When defining a table, you only have to supply an entry for `term` in the heading.</span></span>  
  
 <span data-ttu-id="19325-114">リスト内の各項目を指定した、`<item>`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="19325-114">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="19325-115">定義リストを作成するときに、両方を指定する必要があります`term`と`description`です。</span><span class="sxs-lookup"><span data-stu-id="19325-115">When creating a definition list, you must specify both `term` and `description`.</span></span> <span data-ttu-id="19325-116">ただし、テーブル、箇条書きリスト、または番号付きリストにのみ指定する必要のエントリ`description`です。</span><span class="sxs-lookup"><span data-stu-id="19325-116">However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="19325-117">リストまたはテーブルに指定できるは多く`<item>`に応じてをブロックします。</span><span class="sxs-lookup"><span data-stu-id="19325-117">A list or table can have as many `<item>` blocks as needed.</span></span>  
  
 <span data-ttu-id="19325-118">コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="19325-118">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19325-119">例</span><span class="sxs-lookup"><span data-stu-id="19325-119">Example</span></span>  
 <span data-ttu-id="19325-120">この例では、 `<list>` 「解説」セクションで、箇条書きリストを定義するタグです。</span><span class="sxs-lookup"><span data-stu-id="19325-120">This example uses the `<list>` tag to define a bulleted list in the remarks section.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#5](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/list_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="19325-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="19325-121">See Also</span></span>  
 [<span data-ttu-id="19325-122">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="19325-122">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
