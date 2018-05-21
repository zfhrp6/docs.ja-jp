---
title: '&lt;param&gt; (C# プログラミング ガイド)'
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 3d89637e5b1238c582390750e8eef30960fa90b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ltparamgt-c-programming-guide"></a><span data-ttu-id="fa61b-102">&lt;param&gt; (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="fa61b-102">&lt;param&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="fa61b-103">構文</span><span class="sxs-lookup"><span data-stu-id="fa61b-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fa61b-104">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fa61b-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="fa61b-105">メソッド パラメーターの名前です。</span><span class="sxs-lookup"><span data-stu-id="fa61b-105">The name of a method parameter.</span></span> <span data-ttu-id="fa61b-106">名前は二重引用符 (" ") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="fa61b-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="fa61b-107">パラメーターの説明です。</span><span class="sxs-lookup"><span data-stu-id="fa61b-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa61b-108">コメント</span><span class="sxs-lookup"><span data-stu-id="fa61b-108">Remarks</span></span>  
 <span data-ttu-id="fa61b-109">\<param> タグは、メソッドのいずれか 1 つのパラメーターを説明するためにメソッドの宣言のコメントで使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa61b-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="fa61b-110">複数のパラメーターをドキュメント化するには、複数の \<param> タグを使用します。</span><span class="sxs-lookup"><span data-stu-id="fa61b-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="fa61b-111">\<param> タグのテキストは、IntelliSense、オブジェクト ブラウザー、コード コメント Web レポートに表示されます。</span><span class="sxs-lookup"><span data-stu-id="fa61b-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="fa61b-112">コンパイル時に [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="fa61b-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa61b-113">例</span><span class="sxs-lookup"><span data-stu-id="fa61b-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="fa61b-114">参照</span><span class="sxs-lookup"><span data-stu-id="fa61b-114">See Also</span></span>  
 [<span data-ttu-id="fa61b-115">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="fa61b-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="fa61b-116">ドキュメント コメントとして推奨されるタグ</span><span class="sxs-lookup"><span data-stu-id="fa61b-116">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
