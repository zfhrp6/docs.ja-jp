---
title: ドキュメント コメント用の推奨タグ (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: 54047746db672efbf626eb2d3fc301b341cc49f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338479"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="f4c66-102">ドキュメント コメント用の推奨タグ (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="f4c66-102">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="f4c66-103">コード内のドキュメント コメントは、C# コンパイラによって処理され、**/doc** コマンド ライン オプションで指定した名前のファイルに XML 形式で出力されます。</span><span class="sxs-lookup"><span data-stu-id="f4c66-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="f4c66-104">コンパイラによって生成されたファイルに基づいて最終的なドキュメントを作成するには、カスタム ツールを作成するか、[Sandcastle](https://github.com/EWSoftware/SHFB) などのツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="f4c66-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="f4c66-105">タグは、型や型メンバーなどのコード コンストラクターに対して処理されます。</span><span class="sxs-lookup"><span data-stu-id="f4c66-105">Tags are processed on code constructs such as types and type members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4c66-106">ドキュメント コメントは、名前空間に適用できません。</span><span class="sxs-lookup"><span data-stu-id="f4c66-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="f4c66-107">コンパイラは、有効な XML のタグをすべて処理します。</span><span class="sxs-lookup"><span data-stu-id="f4c66-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="f4c66-108">ユーザー ドキュメントで一般的に使用される機能を提供するタグを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="f4c66-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="f4c66-109">Tags</span><span class="sxs-lookup"><span data-stu-id="f4c66-109">Tags</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="f4c66-110">\<c></span><span class="sxs-lookup"><span data-stu-id="f4c66-110">\<c></span></span>](../../../csharp/programming-guide/xmldoc/code-inline.md)|[<span data-ttu-id="f4c66-111">\<para></span><span class="sxs-lookup"><span data-stu-id="f4c66-111">\<para></span></span>](../../../csharp/programming-guide/xmldoc/para.md)|<span data-ttu-id="f4c66-112">[\<see>](../../../csharp/programming-guide/xmldoc/see.md)\*</span><span class="sxs-lookup"><span data-stu-id="f4c66-112">[\<see>](../../../csharp/programming-guide/xmldoc/see.md)\*</span></span>|  
|[<span data-ttu-id="f4c66-113">\<code></span><span class="sxs-lookup"><span data-stu-id="f4c66-113">\<code></span></span>](../../../csharp/programming-guide/xmldoc/code.md)|<span data-ttu-id="f4c66-114">[\<param>](../../../csharp/programming-guide/xmldoc/param.md)\*</span><span class="sxs-lookup"><span data-stu-id="f4c66-114">[\<param>](../../../csharp/programming-guide/xmldoc/param.md)\*</span></span>|<span data-ttu-id="f4c66-115">[\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md)\*</span><span class="sxs-lookup"><span data-stu-id="f4c66-115">[\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md)\*</span></span>|  
|[<span data-ttu-id="f4c66-116">\<example></span><span class="sxs-lookup"><span data-stu-id="f4c66-116">\<example></span></span>](../../../csharp/programming-guide/xmldoc/example.md)|[<span data-ttu-id="f4c66-117">\<paramref></span><span class="sxs-lookup"><span data-stu-id="f4c66-117">\<paramref></span></span>](../../../csharp/programming-guide/xmldoc/paramref.md)|[<span data-ttu-id="f4c66-118">\<summary></span><span class="sxs-lookup"><span data-stu-id="f4c66-118">\<summary></span></span>](../../../csharp/programming-guide/xmldoc/summary.md)|  
|<span data-ttu-id="f4c66-119">[\<exception>](../../../csharp/programming-guide/xmldoc/exception.md)\*</span><span class="sxs-lookup"><span data-stu-id="f4c66-119">[\<exception>](../../../csharp/programming-guide/xmldoc/exception.md)\*</span></span>|<span data-ttu-id="f4c66-120">[\<permission>](../../../csharp/programming-guide/xmldoc/permission.md)\*</span><span class="sxs-lookup"><span data-stu-id="f4c66-120">[\<permission>](../../../csharp/programming-guide/xmldoc/permission.md)\*</span></span>|<span data-ttu-id="f4c66-121">[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)\*</span><span class="sxs-lookup"><span data-stu-id="f4c66-121">[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)\*</span></span>|  
|<span data-ttu-id="f4c66-122">[\<include>](../../../csharp/programming-guide/xmldoc/include.md)\*</span><span class="sxs-lookup"><span data-stu-id="f4c66-122">[\<include>](../../../csharp/programming-guide/xmldoc/include.md)\*</span></span>|[<span data-ttu-id="f4c66-123">\<remarks></span><span class="sxs-lookup"><span data-stu-id="f4c66-123">\<remarks></span></span>](../../../csharp/programming-guide/xmldoc/remarks.md)|[<span data-ttu-id="f4c66-124">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="f4c66-124">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)|  
|[<span data-ttu-id="f4c66-125">\<list></span><span class="sxs-lookup"><span data-stu-id="f4c66-125">\<list></span></span>](../../../csharp/programming-guide/xmldoc/list.md)|[<span data-ttu-id="f4c66-126">\<returns></span><span class="sxs-lookup"><span data-stu-id="f4c66-126">\<returns></span></span>](../../../csharp/programming-guide/xmldoc/returns.md)|[<span data-ttu-id="f4c66-127">\<value></span><span class="sxs-lookup"><span data-stu-id="f4c66-127">\<value></span></span>](../../../csharp/programming-guide/xmldoc/value.md)|  
  
 <span data-ttu-id="f4c66-128">(\* は、コンパイラが構文を検証することを示します。)</span><span class="sxs-lookup"><span data-stu-id="f4c66-128">(\* denotes that the compiler verifies syntax.)</span></span>  
  
 <span data-ttu-id="f4c66-129">ドキュメント コメントのテキストに山かっこを表示する場合は、次の例に示すように `<` と `>` を使用します。</span><span class="sxs-lookup"><span data-stu-id="f4c66-129">If you want angle brackets to appear in the text of a documentation comment, use `<` and `>`, as shown in the following example.</span></span>  
  
```xml  
/// <summary cref="C < T >">  
/// </summary>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4c66-130">参照</span><span class="sxs-lookup"><span data-stu-id="f4c66-130">See Also</span></span>  
 [<span data-ttu-id="f4c66-131">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="f4c66-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f4c66-132">/doc (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="f4c66-132">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [<span data-ttu-id="f4c66-133">XML ドキュメント コメント</span><span class="sxs-lookup"><span data-stu-id="f4c66-133">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
