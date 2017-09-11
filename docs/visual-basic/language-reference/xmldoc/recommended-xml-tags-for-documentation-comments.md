---
title: "ドキュメント コメント (Visual Basic) の推奨される XML タグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlDocComment
dev_langs:
- VB
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e4a6c3128a69e8d666d44882ef3eac9f9a31a51a
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="f1964-102">ドキュメント コメントとして推奨される XML タグ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1964-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="f1964-103">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラは、XML ファイルに、コードのドキュメント コメントを処理します。</span><span class="sxs-lookup"><span data-stu-id="f1964-103">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="f1964-104">その他のツールを使用して、ドキュメントを XML ファイルに変換することができます。</span><span class="sxs-lookup"><span data-stu-id="f1964-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="f1964-105">XML コメントは、型などのコード コンス トラクターでは許可し、メンバーを入力します。</span><span class="sxs-lookup"><span data-stu-id="f1964-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="f1964-106">部分型の型の一部にすぎませんことができます XML コメントが、そのメンバーの注釈に制限はありません。</span><span class="sxs-lookup"><span data-stu-id="f1964-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1964-107">ドキュメントのコメントは、名前空間には適用できません。</span><span class="sxs-lookup"><span data-stu-id="f1964-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="f1964-108">理由は、1 つの名前空間がいくつかのアセンブリにまたがることができ、すべてのアセンブリを同時に読み込まれる必要があることです。</span><span class="sxs-lookup"><span data-stu-id="f1964-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="f1964-109">コンパイラは、有効な XML は、任意のタグを処理します。</span><span class="sxs-lookup"><span data-stu-id="f1964-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="f1964-110">次のタグは、ユーザー ドキュメントでよく使用される機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="f1964-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="f1964-111">\<c ></span><span class="sxs-lookup"><span data-stu-id="f1964-111">\<c></span></span>](../../../visual-basic/language-reference/xmldoc/c.md)|[<span data-ttu-id="f1964-112">\<コード ></span><span class="sxs-lookup"><span data-stu-id="f1964-112">\<code></span></span>](../../../visual-basic/language-reference/xmldoc/code.md)|[<span data-ttu-id="f1964-113">\<例 ></span><span class="sxs-lookup"><span data-stu-id="f1964-113">\<example></span></span>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|<span data-ttu-id="f1964-114">[\<例外 >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f1964-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span></span>|<span data-ttu-id="f1964-115">[\<含める >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f1964-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span></span>|[<span data-ttu-id="f1964-116">\<list></span><span class="sxs-lookup"><span data-stu-id="f1964-116">\<list></span></span>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[<span data-ttu-id="f1964-117">\<para ></span><span class="sxs-lookup"><span data-stu-id="f1964-117">\<para></span></span>](../../../visual-basic/language-reference/xmldoc/para.md)|<span data-ttu-id="f1964-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f1964-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span></span>|[<span data-ttu-id="f1964-119">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="f1964-119">\<paramref></span></span>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|<span data-ttu-id="f1964-120">[\<アクセス許可 >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f1964-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span></span>|[<span data-ttu-id="f1964-121">\<「解説」></span><span class="sxs-lookup"><span data-stu-id="f1964-121">\<remarks></span></span>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[<span data-ttu-id="f1964-122">\<返します ></span><span class="sxs-lookup"><span data-stu-id="f1964-122">\<returns></span></span>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|<span data-ttu-id="f1964-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f1964-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span></span>|<span data-ttu-id="f1964-124">[\<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f1964-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span></span>|[<span data-ttu-id="f1964-125">\<概要 ></span><span class="sxs-lookup"><span data-stu-id="f1964-125">\<summary></span></span>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|<span data-ttu-id="f1964-126">[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f1964-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span></span>|[<span data-ttu-id="f1964-127">\<値 ></span><span class="sxs-lookup"><span data-stu-id="f1964-127">\<value></span></span>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 <span data-ttu-id="f1964-128">(<sup>1</sup>コンパイラが構文を検証します)。</span><span class="sxs-lookup"><span data-stu-id="f1964-128">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1964-129">ドキュメント コメントのテキスト内に山かっこを実行する場合に、使用`<`と`>`です。</span><span class="sxs-lookup"><span data-stu-id="f1964-129">If you want angle brackets to appear in the text of a documentation comment, use `<` and `>`.</span></span> <span data-ttu-id="f1964-130">たとえば、文字列`"<text in angle brackets>"`でサポートされる`<text in angle``brackets>`します。</span><span class="sxs-lookup"><span data-stu-id="f1964-130">For example, the string `"<text in angle brackets>"` will appear as `<text in angle``brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1964-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1964-131">See Also</span></span>  
 <span data-ttu-id="f1964-132">[XML を使用してコードを文書化します。](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) </span><span class="sxs-lookup"><span data-stu-id="f1964-132">[Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) </span></span>  
<span data-ttu-id="f1964-133"> [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) </span><span class="sxs-lookup"><span data-stu-id="f1964-133"> [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) </span></span>  
<span data-ttu-id="f1964-134"> [方法: XML ドキュメントを作成する](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)</span><span class="sxs-lookup"><span data-stu-id="f1964-134"> [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)</span></span>
