---
title: "&lt;typeparam&gt; (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- typeparam
dev_langs:
- CSharp
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
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
ms.openlocfilehash: 8bb1d13976cf2cc9df4f573702168c6abdfff3d5
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="lttypeparamgt-c-programming-guide"></a><span data-ttu-id="03f74-102">&lt;typeparam&gt; (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="03f74-102">&lt;typeparam&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="03f74-103">構文</span><span class="sxs-lookup"><span data-stu-id="03f74-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="03f74-104">パラメーター</span><span class="sxs-lookup"><span data-stu-id="03f74-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="03f74-105">型パラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="03f74-105">The name of the type parameter.</span></span> <span data-ttu-id="03f74-106">名前は二重引用符 (" ") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="03f74-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="03f74-107">型パラメーターの説明。</span><span class="sxs-lookup"><span data-stu-id="03f74-107">A description for the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03f74-108">コメント</span><span class="sxs-lookup"><span data-stu-id="03f74-108">Remarks</span></span>  
 <span data-ttu-id="03f74-109">`<typeparam>` タグは、型パラメーターを説明するためにジェネリック型またはメソッドの宣言のコメントで使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="03f74-109">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="03f74-110">ジェネリック型またはメソッドの型パラメーターごとにタグを追加します。</span><span class="sxs-lookup"><span data-stu-id="03f74-110">Add a tag for each type parameter of the generic type or method.</span></span>  
  
 <span data-ttu-id="03f74-111">詳細については、「[ジェネリック](../../../csharp/programming-guide/generics/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03f74-111">For more information, see [Generics](../../../csharp/programming-guide/generics/index.md).</span></span>  
  
 <span data-ttu-id="03f74-112">`<typeparam>` タグのテキストは、IntelliSense、[オブジェクト ブラウザー ウィンドウ](http://msdn.microsoft.com/en-us/3c7f1673-1f0d-41b1-94ca-a3dcfcb82cda)、コード コメント Web レポートに表示されます。</span><span class="sxs-lookup"><span data-stu-id="03f74-112">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](http://msdn.microsoft.com/en-us/3c7f1673-1f0d-41b1-94ca-a3dcfcb82cda) code comment web report.</span></span>  
  
 <span data-ttu-id="03f74-113">コンパイル時に [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="03f74-113">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03f74-114">例</span><span class="sxs-lookup"><span data-stu-id="03f74-114">Example</span></span>  
 <span data-ttu-id="03f74-115">[!code-cs[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparam_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="03f74-115">[!code-cs[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparam_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03f74-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="03f74-116">See Also</span></span>  
 <span data-ttu-id="03f74-117">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="03f74-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="03f74-118">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="03f74-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="03f74-119">ドキュメント コメントとして推奨されるタグ</span><span class="sxs-lookup"><span data-stu-id="03f74-119">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

