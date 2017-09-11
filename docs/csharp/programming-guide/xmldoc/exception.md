---
title: "&lt;例外&gt; (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- exception
- <exception>
dev_langs:
- CSharp
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
caps.latest.revision: 16
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
ms.openlocfilehash: bdcbe116db4ed0f63ea73c524c482266b4ac1a38
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="ltexceptiongt-c-programming-guide"></a><span data-ttu-id="23f54-102">&lt;例外&gt; (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="23f54-102">&lt;exception&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="23f54-103">構文</span><span class="sxs-lookup"><span data-stu-id="23f54-103">Syntax</span></span>  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="23f54-104">パラメーター</span><span class="sxs-lookup"><span data-stu-id="23f54-104">Parameters</span></span>  
 <span data-ttu-id="23f54-105">cref = "`member`"</span><span class="sxs-lookup"><span data-stu-id="23f54-105">cref = " `member`"</span></span>  
 <span data-ttu-id="23f54-106">現在のコンパイル環境から使用できる例外の参照。</span><span class="sxs-lookup"><span data-stu-id="23f54-106">A reference to an exception that is available from the current compilation environment.</span></span> <span data-ttu-id="23f54-107">コンパイラは、指定された例外が存在し、出力の XML で `member` が正規要素名に変換されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="23f54-107">The compiler checks that the given exception exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="23f54-108">`member` は、二重引用符 (" ") で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="23f54-108">`member` must appear within double quotation marks (" ").</span></span>  
  
 <span data-ttu-id="23f54-109">ジェネリック型への cref 参照を作成する方法については、[\<see>](../../../csharp/programming-guide/xmldoc/see.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23f54-109">For more information on how to create a cref reference to a generic type, see [\<see>](../../../csharp/programming-guide/xmldoc/see.md).</span></span>  
  
 `description`  
 <span data-ttu-id="23f54-110">例外の説明。</span><span class="sxs-lookup"><span data-stu-id="23f54-110">A description of the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23f54-111">コメント</span><span class="sxs-lookup"><span data-stu-id="23f54-111">Remarks</span></span>  
 <span data-ttu-id="23f54-112">\<exception> タグを使用すると、スローできる例外を指定できます。</span><span class="sxs-lookup"><span data-stu-id="23f54-112">The \<exception> tag lets you specify which exceptions can be thrown.</span></span> <span data-ttu-id="23f54-113">このタブは、メソッド、プロパティ、イベント、インデクサーの定義に適用できます。</span><span class="sxs-lookup"><span data-stu-id="23f54-113">This tag can be applied to definitions for methods, properties, events, and indexers.</span></span>  
  
 <span data-ttu-id="23f54-114">コンパイル時に [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定してドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="23f54-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
 <span data-ttu-id="23f54-115">例外処理の詳細については、「[例外と例外処理](../../../csharp/programming-guide/exceptions/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23f54-115">For more information about exception handling, see [Exceptions and Exception Handling](../../../csharp/programming-guide/exceptions/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="23f54-116">例</span><span class="sxs-lookup"><span data-stu-id="23f54-116">Example</span></span>  
 <span data-ttu-id="23f54-117">[!code-cs[csProgGuideDocComments#4](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/exception_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="23f54-117">[!code-cs[csProgGuideDocComments#4](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/exception_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23f54-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="23f54-118">See Also</span></span>  
 <span data-ttu-id="23f54-119">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="23f54-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="23f54-120">ドキュメント コメントとして推奨されるタグ</span><span class="sxs-lookup"><span data-stu-id="23f54-120">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

