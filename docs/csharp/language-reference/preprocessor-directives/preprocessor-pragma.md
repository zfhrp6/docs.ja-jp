---
title: '#pragma (C# リファレンス)'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: a4829d5062474922d45a2f4f8e1cddf9023b6ad8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33278810"
---
# <a name="pragma-c-reference"></a><span data-ttu-id="994ca-102">#pragma (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="994ca-102">#pragma (C# Reference)</span></span>
<span data-ttu-id="994ca-103">`#pragma` は、ファイル内に指定され、そのファイルのコンパイルについての特別な命令をコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="994ca-103">`#pragma` gives the compiler special instructions for the compilation of the file in which it appears.</span></span> <span data-ttu-id="994ca-104">命令はコンパイラによってサポートされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="994ca-104">The instructions must be supported by the compiler.</span></span> <span data-ttu-id="994ca-105">つまり、`#pragma` を使用してカスタムの前処理命令を作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="994ca-105">In other words, you cannot use `#pragma` to create custom preprocessing instructions.</span></span> <span data-ttu-id="994ca-106">Microsoft C# コンパイラは、次の 2 つの `#pragma` 命令をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="994ca-106">The Microsoft C# compiler supports the following two `#pragma` instructions:</span></span>  
  
 [<span data-ttu-id="994ca-107">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="994ca-107">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [<span data-ttu-id="994ca-108">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="994ca-108">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a><span data-ttu-id="994ca-109">構文</span><span class="sxs-lookup"><span data-stu-id="994ca-109">Syntax</span></span>  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
#### <a name="parameters"></a><span data-ttu-id="994ca-110">パラメーター</span><span class="sxs-lookup"><span data-stu-id="994ca-110">Parameters</span></span>  
 `pragma-name`  
 <span data-ttu-id="994ca-111">認識されているプラグマの名前。</span><span class="sxs-lookup"><span data-stu-id="994ca-111">The name of a recognized pragma.</span></span>  
  
 `pragma-arguments`  
 <span data-ttu-id="994ca-112">プラグマに固有の引数。</span><span class="sxs-lookup"><span data-stu-id="994ca-112">Pragma-specific arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="994ca-113">参照</span><span class="sxs-lookup"><span data-stu-id="994ca-113">See Also</span></span>  
 [<span data-ttu-id="994ca-114">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="994ca-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="994ca-115">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="994ca-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="994ca-116">C# プリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="994ca-116">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [<span data-ttu-id="994ca-117">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="994ca-117">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
 [<span data-ttu-id="994ca-118">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="994ca-118">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)
