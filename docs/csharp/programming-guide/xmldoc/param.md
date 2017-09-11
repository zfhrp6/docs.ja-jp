---
title: "&lt;param&gt; (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- param
- <param>
dev_langs:
- CSharp
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
caps.latest.revision: 15
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
ms.openlocfilehash: 1076405d60c85540eeaeba39821bd20bc628030d
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="ltparamgt-c-programming-guide"></a><span data-ttu-id="b5cbf-102">&lt;param&gt; (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="b5cbf-102">&lt;param&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="b5cbf-103">構文</span><span class="sxs-lookup"><span data-stu-id="b5cbf-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b5cbf-104">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b5cbf-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="b5cbf-105">メソッド パラメーターの名前です。</span><span class="sxs-lookup"><span data-stu-id="b5cbf-105">The name of a method parameter.</span></span> <span data-ttu-id="b5cbf-106">名前は二重引用符 (" ") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="b5cbf-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="b5cbf-107">パラメーターの説明です。</span><span class="sxs-lookup"><span data-stu-id="b5cbf-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5cbf-108">コメント</span><span class="sxs-lookup"><span data-stu-id="b5cbf-108">Remarks</span></span>  
 <span data-ttu-id="b5cbf-109">\<param> タグは、メソッドのいずれか 1 つのパラメーターを説明するためにメソッドの宣言のコメントで使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5cbf-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="b5cbf-110">複数のパラメーターをドキュメント化するには、複数の \<param> タグを使用します。</span><span class="sxs-lookup"><span data-stu-id="b5cbf-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="b5cbf-111">\<param> タグのテキストは、IntelliSense、オブジェクト ブラウザー、コード コメント Web レポートに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b5cbf-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="b5cbf-112">コンパイル時に [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="b5cbf-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5cbf-113">例</span><span class="sxs-lookup"><span data-stu-id="b5cbf-113">Example</span></span>  
 <span data-ttu-id="b5cbf-114">[!code-cs[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b5cbf-114">[!code-cs[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5cbf-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="b5cbf-115">See Also</span></span>  
 <span data-ttu-id="b5cbf-116">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b5cbf-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="b5cbf-117">ドキュメント コメントとして推奨されるタグ</span><span class="sxs-lookup"><span data-stu-id="b5cbf-117">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

