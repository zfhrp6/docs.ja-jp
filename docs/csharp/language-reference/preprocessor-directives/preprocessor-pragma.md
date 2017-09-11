---
title: "#<a name=\"pragma-c-reference\"></a>pragma (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#pragma'
dev_langs:
- CSharp
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
caps.latest.revision: 18
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
ms.openlocfilehash: e03fc387b105c1dee3b7fed93263ad8ef22d5934
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="pragma-c-reference"></a><span data-ttu-id="d765c-102">#pragma (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="d765c-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="d765c-103">`#pragma` は、ファイル内に指定され、そのファイルのコンパイルについての特別な命令をコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="d765c-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="d765c-104">命令はコンパイラによってサポートされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d765c-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="d765c-105">つまり、`#pragma` を使用してカスタムの前処理命令を作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="d765c-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="d765c-106">Microsoft C# コンパイラは、次の 2 つの `#pragma` 命令をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="d765c-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="d765c-107">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="d765c-107">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="d765c-108">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="d765c-108">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="d765c-109">構文</span><span class="sxs-lookup"><span data-stu-id="d765c-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d765c-110">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d765c-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="d765c-111">認識されているプラグマの名前。</span><span class="sxs-lookup"><span data-stu-id="d765c-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="d765c-112">プラグマに固有の引数。</span><span class="sxs-lookup"><span data-stu-id="d765c-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d765c-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="d765c-113">See Also</span></span>  
 <span data-ttu-id="d765c-114">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="d765c-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="d765c-115">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d765c-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="d765c-116">[C# プリプロセッサ ディレクティブ](../../../csharp/language-reference/preprocessor-directives/index.md) </span><span class="sxs-lookup"><span data-stu-id="d765c-116">[C# Preprocessor Directives](../../../csharp/language-reference/preprocessor-directives/index.md) </span></span>  
 <span data-ttu-id="d765c-117">[#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) </span><span class="sxs-lookup"><span data-stu-id="d765c-117">[#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) </span></span>  
 [<span data-ttu-id="d765c-118">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="d765c-118">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)

