---
title: '&lt;typeparam&gt; (C# プログラミング ガイド)'
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 8c7fc1aba05af731d3df80e0b10c2981b5784197
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="lttypeparamgt-c-programming-guide"></a><span data-ttu-id="83644-102">&lt;typeparam&gt; (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="83644-102">&lt;typeparam&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="83644-103">構文</span><span class="sxs-lookup"><span data-stu-id="83644-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83644-104">パラメーター</span><span class="sxs-lookup"><span data-stu-id="83644-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="83644-105">型パラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="83644-105">The name of the type parameter.</span></span> <span data-ttu-id="83644-106">名前は二重引用符 (" ") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="83644-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="83644-107">型パラメーターの説明。</span><span class="sxs-lookup"><span data-stu-id="83644-107">A description for the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83644-108">コメント</span><span class="sxs-lookup"><span data-stu-id="83644-108">Remarks</span></span>  
 <span data-ttu-id="83644-109">`<typeparam>` タグは、型パラメーターを説明するためにジェネリック型またはメソッドの宣言のコメントで使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="83644-109">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="83644-110">ジェネリック型またはメソッドの型パラメーターごとにタグを追加します。</span><span class="sxs-lookup"><span data-stu-id="83644-110">Add a tag for each type parameter of the generic type or method.</span></span>  
  
 <span data-ttu-id="83644-111">詳細については、「[ジェネリック](../../../csharp/programming-guide/generics/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83644-111">For more information, see [Generics](../../../csharp/programming-guide/generics/index.md).</span></span>  
  
 <span data-ttu-id="83644-112">`<typeparam>` タグのテキストは、IntelliSense、[オブジェクト ブラウザー ウィンドウ](http://msdn.microsoft.com/library/3c7f1673-1f0d-41b1-94ca-a3dcfcb82cda)、コード コメント Web レポートに表示されます。</span><span class="sxs-lookup"><span data-stu-id="83644-112">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](http://msdn.microsoft.com/library/3c7f1673-1f0d-41b1-94ca-a3dcfcb82cda) code comment web report.</span></span>  
  
 <span data-ttu-id="83644-113">コンパイル時に [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="83644-113">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83644-114">例</span><span class="sxs-lookup"><span data-stu-id="83644-114">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparam_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="83644-115">参照</span><span class="sxs-lookup"><span data-stu-id="83644-115">See Also</span></span>  
 [<span data-ttu-id="83644-116">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="83644-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="83644-117">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="83644-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="83644-118">ドキュメント コメントとして推奨されるタグ</span><span class="sxs-lookup"><span data-stu-id="83644-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
