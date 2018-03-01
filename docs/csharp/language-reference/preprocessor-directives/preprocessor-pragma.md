---
title: "#pragma (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6f53bd0ed3f35f049b0a1cbb21c5b9a563f9fce9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="pragma-c-reference"></a><span data-ttu-id="dd0c5-102">#pragma (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="dd0c5-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="dd0c5-103">`#pragma` は、ファイル内に指定され、そのファイルのコンパイルについての特別な命令をコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="dd0c5-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="dd0c5-104">命令はコンパイラによってサポートされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="dd0c5-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="dd0c5-105">つまり、`#pragma` を使用してカスタムの前処理命令を作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="dd0c5-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="dd0c5-106">Microsoft C# コンパイラは、次の 2 つの `#pragma` 命令をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="dd0c5-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="dd0c5-107">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="dd0c5-107">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="dd0c5-108">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="dd0c5-108">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="dd0c5-109">構文</span><span class="sxs-lookup"><span data-stu-id="dd0c5-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dd0c5-110">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dd0c5-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="dd0c5-111">認識されているプラグマの名前。</span><span class="sxs-lookup"><span data-stu-id="dd0c5-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="dd0c5-112">プラグマに固有の引数。</span><span class="sxs-lookup"><span data-stu-id="dd0c5-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd0c5-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd0c5-113">See Also</span></span>  
 [<span data-ttu-id="dd0c5-114">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="dd0c5-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="dd0c5-115">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="dd0c5-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="dd0c5-116">C# プリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="dd0c5-116">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [<span data-ttu-id="dd0c5-117">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="dd0c5-117">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
 [<span data-ttu-id="dd0c5-118">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="dd0c5-118">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)
