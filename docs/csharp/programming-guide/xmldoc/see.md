---
title: "&lt;see&gt; (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <see>
- see
dev_langs:
- CSharp
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
caps.latest.revision: 19
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
ms.openlocfilehash: 831caae9574c25f16e8b2ede734746f48019198e
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="ltseegt-c-programming-guide"></a><span data-ttu-id="692c7-102">&lt;see&gt; (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="692c7-102">&lt;see&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="692c7-103">構文</span><span class="sxs-lookup"><span data-stu-id="692c7-103">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="692c7-104">パラメーター</span><span class="sxs-lookup"><span data-stu-id="692c7-104">Parameters</span></span>  
 <span data-ttu-id="692c7-105">cref = "`member`"</span><span class="sxs-lookup"><span data-stu-id="692c7-105">cref = " `member`"</span></span>  
 <span data-ttu-id="692c7-106">現在のコンパイル環境からの呼び出しに利用できる、メンバーまたはフィールドへの参照。</span><span class="sxs-lookup"><span data-stu-id="692c7-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="692c7-107">コンパイラは、指定されたコード要素が存在するかどうかを確認し、`member` を出力 XML 内の要素名に渡します。*member* は二重引用符で囲んで配置します。</span><span class="sxs-lookup"><span data-stu-id="692c7-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.Place *member* within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="692c7-108">コメント</span><span class="sxs-lookup"><span data-stu-id="692c7-108">Remarks</span></span>  
 <span data-ttu-id="692c7-109">\<see> タグを使用すると、テキスト内でリンクを指定できます。</span><span class="sxs-lookup"><span data-stu-id="692c7-109">The \<see> tag lets you specify a link from within text.</span></span> <span data-ttu-id="692c7-110">テキストが参照セクションに配置されていることを示すには、[\<<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="692c7-110">Use [\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="692c7-111">コード要素のドキュメント ページへの内部ハイパーリンクを作成するには、[cref 属性](../../../csharp/programming-guide/xmldoc/cref-attribute.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="692c7-111">Use the [cref Attribute](../../../csharp/programming-guide/xmldoc/cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span>  
  
 <span data-ttu-id="692c7-112">コンパイル時に [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="692c7-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="692c7-113">次の例では、summary セクション内の \<see> タグを示しています。</span><span class="sxs-lookup"><span data-stu-id="692c7-113">The following example shows a \<see> tag within a summary section.</span></span>  
  
 <span data-ttu-id="692c7-114">[!code-cs[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/see_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="692c7-114">[!code-cs[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/see_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="692c7-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="692c7-115">See Also</span></span>  
 <span data-ttu-id="692c7-116">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="692c7-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="692c7-117">ドキュメント コメントとして推奨されるタグ</span><span class="sxs-lookup"><span data-stu-id="692c7-117">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

