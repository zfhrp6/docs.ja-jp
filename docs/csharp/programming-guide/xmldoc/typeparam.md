---
title: "&lt;typeparam&gt; (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e1b8800e39b1ee5eeac8c5d3e4390ed3226b33a3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="lttypeparamgt-c-programming-guide"></a><span data-ttu-id="c337a-102">&lt;typeparam&gt; (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="c337a-102">&lt;typeparam&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="c337a-103">構文</span><span class="sxs-lookup"><span data-stu-id="c337a-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c337a-104">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c337a-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="c337a-105">型パラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="c337a-105">The name of the type parameter.</span></span> <span data-ttu-id="c337a-106">名前は二重引用符 (" ") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="c337a-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="c337a-107">型パラメーターの説明。</span><span class="sxs-lookup"><span data-stu-id="c337a-107">A description for the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c337a-108">コメント</span><span class="sxs-lookup"><span data-stu-id="c337a-108">Remarks</span></span>  
 <span data-ttu-id="c337a-109">`<typeparam>` タグは、型パラメーターを説明するためにジェネリック型またはメソッドの宣言のコメントで使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c337a-109">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="c337a-110">ジェネリック型またはメソッドの型パラメーターごとにタグを追加します。</span><span class="sxs-lookup"><span data-stu-id="c337a-110">Add a tag for each type parameter of the generic type or method.</span></span>  
  
 <span data-ttu-id="c337a-111">詳細については、「[ジェネリック](../../../csharp/programming-guide/generics/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c337a-111">For more information, see [Generics](../../../csharp/programming-guide/generics/index.md).</span></span>  
  
 <span data-ttu-id="c337a-112">`<typeparam>` タグのテキストは、IntelliSense、[オブジェクト ブラウザー ウィンドウ](http://msdn.microsoft.com/library/3c7f1673-1f0d-41b1-94ca-a3dcfcb82cda)、コード コメント Web レポートに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c337a-112">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](http://msdn.microsoft.com/library/3c7f1673-1f0d-41b1-94ca-a3dcfcb82cda) code comment web report.</span></span>  
  
 <span data-ttu-id="c337a-113">コンパイル時に [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="c337a-113">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c337a-114">例</span><span class="sxs-lookup"><span data-stu-id="c337a-114">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparam_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c337a-115">参照</span><span class="sxs-lookup"><span data-stu-id="c337a-115">See Also</span></span>  
 [<span data-ttu-id="c337a-116">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="c337a-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c337a-117">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="c337a-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c337a-118">ドキュメント コメントとして推奨されるタグ</span><span class="sxs-lookup"><span data-stu-id="c337a-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
