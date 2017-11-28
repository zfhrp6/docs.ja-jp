---
title: "&lt;c&gt; (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 21c7830c03b0b93e3597835954ac9e7d2feb49e9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltcgt-c-programming-guide"></a><span data-ttu-id="cdd04-102">&lt;c&gt; (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="cdd04-102">&lt;c&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="cdd04-103">構文</span><span class="sxs-lookup"><span data-stu-id="cdd04-103">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cdd04-104">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cdd04-104">Parameters</span></span>  
 `text`  
 <span data-ttu-id="cdd04-105">コードとして指定するテキストです。</span><span class="sxs-lookup"><span data-stu-id="cdd04-105">The text you would like to indicate as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cdd04-106">コメント</span><span class="sxs-lookup"><span data-stu-id="cdd04-106">Remarks</span></span>  
 <span data-ttu-id="cdd04-107">\<c> タグを使用すると、説明内のテキストをコードとして指定できます。</span><span class="sxs-lookup"><span data-stu-id="cdd04-107">The \<c> tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="cdd04-108">複数行をコードとして指定する場合は、[\<code>](../../../csharp/programming-guide/xmldoc/code.md) タグを使用します。</span><span class="sxs-lookup"><span data-stu-id="cdd04-108">Use [\<code>](../../../csharp/programming-guide/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="cdd04-109">コンパイル時に [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="cdd04-109">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdd04-110">例</span><span class="sxs-lookup"><span data-stu-id="cdd04-110">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#2](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/code-inline_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="cdd04-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="cdd04-111">See Also</span></span>  
 [<span data-ttu-id="cdd04-112">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="cdd04-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cdd04-113">ドキュメント コメントとして推奨されるタグ</span><span class="sxs-lookup"><span data-stu-id="cdd04-113">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
