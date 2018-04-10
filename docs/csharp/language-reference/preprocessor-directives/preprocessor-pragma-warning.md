---
title: '#pragma warning (C# リファレンス)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5330b448dc2b328992b2d29699557d20df56dee4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="pragma-warning-c-reference"></a><span data-ttu-id="363b1-102">#pragma 警告 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="363b1-102">#pragma warning (C# Reference)</span></span>
<span data-ttu-id="363b1-103">`#pragma warning` を使用すると、特定の警告を有効または無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="363b1-103">`#pragma warning` can enable or disable certain warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="363b1-104">構文</span><span class="sxs-lookup"><span data-stu-id="363b1-104">Syntax</span></span>  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
#### <a name="parameters"></a><span data-ttu-id="363b1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="363b1-105">Parameters</span></span>  
 `warning-list`  
 <span data-ttu-id="363b1-106">警告番号のコンマ区切りのリスト。</span><span class="sxs-lookup"><span data-stu-id="363b1-106">A comma-separated list of warning numbers.</span></span> <span data-ttu-id="363b1-107">"CS" というプレフィックスは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="363b1-107">The "CS" prefix is optional.</span></span>  
  
 <span data-ttu-id="363b1-108">警告番号が指定されていないと、`disable` はすべての警告を無効にし、`restore` はすべての警告を有効にします。</span><span class="sxs-lookup"><span data-stu-id="363b1-108">When no warning numbers are specified, `disable` disables all warnings and `restore` enables all warnings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="363b1-109">Visual Studio で警告番号を調べるには、プロジェクトをビルドし、**[出力]** ウィンドウで警告番号を探してください。</span><span class="sxs-lookup"><span data-stu-id="363b1-109">To find warning numbers in Visual Studio, build your project and then look for the warning numbers in the **Output** window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="363b1-110">例</span><span class="sxs-lookup"><span data-stu-id="363b1-110">Example</span></span>  
  
```csharp
// pragma_warning.cs  
using System;  
  
#pragma warning disable 414, CS3021  
[CLSCompliant(false)]  
public class C  
{  
    int i = 1;  
    static void Main()  
    {  
    }  
}  
#pragma warning restore CS3021  
[CLSCompliant(false)]  // CS3021  
public class D  
{  
    int i = 1;  
    public static void F()  
    {  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="363b1-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="363b1-111">See Also</span></span>  
 [<span data-ttu-id="363b1-112">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="363b1-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="363b1-113">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="363b1-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="363b1-114">C# プリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="363b1-114">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [<span data-ttu-id="363b1-115">C# コンパイラ エラー</span><span class="sxs-lookup"><span data-stu-id="363b1-115">C# Compiler Errors</span></span>](../../../csharp/language-reference/compiler-messages/index.md)
