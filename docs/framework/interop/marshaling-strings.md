---
title: "文字列のマーシャリング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- marshaling, samples
- platform invoke, marshaling data
- data marshaling, strings
- data marshaling, samples
- data marshaling, platform invoke
- marshaling. strings
- marshaling, platform invoke
- sample applications [.NET Framework], marshaling strings
ms.assetid: e21b078b-70fb-4905-be26-c097ab2433ff
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 750f4e6852cd5aa52d03f884edcbfbf80ed5fab5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="marshaling-strings"></a><span data-ttu-id="63fbe-102">文字列のマーシャリング</span><span class="sxs-lookup"><span data-stu-id="63fbe-102">Marshaling Strings</span></span>
<span data-ttu-id="63fbe-103">プラットフォーム呼び出しは、文字列のパラメーターをコピーし、必要な場合は、.NET Framework 形式 (Unicode) からアンマネージ形式 (ANSI) に変換します。</span><span class="sxs-lookup"><span data-stu-id="63fbe-103">Platform invoke copies string parameters, converting them from the .NET Framework format (Unicode) to the unmanaged format (ANSI), if needed.</span></span> <span data-ttu-id="63fbe-104">マネージ文字列は変更できないため、プラットフォーム呼び出しでは、関数から戻るときに、アンマネージ メモリからマネージ メモリに文字列がコピーされて戻されることはありません。</span><span class="sxs-lookup"><span data-stu-id="63fbe-104">Because managed strings are immutable, platform invoke does not copy them back from unmanaged memory to managed memory when the function returns.</span></span>  
  
 <span data-ttu-id="63fbe-105">次の表では、文字列のマーシャリング オプションの一覧、それぞれの使用方法の説明、対応する .NET Framework サンプルへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="63fbe-105">The following table lists marshaling options for strings, describes their usage, and provides a link to the corresponding .NET Framework sample.</span></span>  
  
|<span data-ttu-id="63fbe-106">String</span><span class="sxs-lookup"><span data-stu-id="63fbe-106">String</span></span>|<span data-ttu-id="63fbe-107">説明</span><span class="sxs-lookup"><span data-stu-id="63fbe-107">Description</span></span>|<span data-ttu-id="63fbe-108">サンプル</span><span class="sxs-lookup"><span data-stu-id="63fbe-108">Sample</span></span>|  
|------------|-----------------|------------|  
|<span data-ttu-id="63fbe-109">値渡し。</span><span class="sxs-lookup"><span data-stu-id="63fbe-109">By value.</span></span>|<span data-ttu-id="63fbe-110">In パラメーターとして文字列を渡します。</span><span class="sxs-lookup"><span data-stu-id="63fbe-110">Passes strings as In parameters.</span></span>|[<span data-ttu-id="63fbe-111">MsgBox</span><span class="sxs-lookup"><span data-stu-id="63fbe-111">MsgBox</span></span>](../../../docs/framework/interop/msgbox-sample.md)|  
|<span data-ttu-id="63fbe-112">結果として。</span><span class="sxs-lookup"><span data-stu-id="63fbe-112">As result.</span></span>|<span data-ttu-id="63fbe-113">アンマネージ コードから文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="63fbe-113">Returns strings from unmanaged code.</span></span>|[<span data-ttu-id="63fbe-114">文字列</span><span class="sxs-lookup"><span data-stu-id="63fbe-114">Strings</span></span>](http://msdn.microsoft.com/en-us/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|<span data-ttu-id="63fbe-115">参照渡し。</span><span class="sxs-lookup"><span data-stu-id="63fbe-115">By reference.</span></span>|<span data-ttu-id="63fbe-116"><xref:System.Text.StringBuilder> を使って In/Out パラメーターとして文字列を渡します。</span><span class="sxs-lookup"><span data-stu-id="63fbe-116">Passes strings as In/Out parameters using <xref:System.Text.StringBuilder>.</span></span>|[<span data-ttu-id="63fbe-117">バッファー</span><span class="sxs-lookup"><span data-stu-id="63fbe-117">Buffers</span></span>](http://msdn.microsoft.com/en-us/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5)|  
|<span data-ttu-id="63fbe-118">構造体で値渡し。</span><span class="sxs-lookup"><span data-stu-id="63fbe-118">In a structure by value.</span></span>|<span data-ttu-id="63fbe-119">In パラメーターである構造体で文字列を渡します。</span><span class="sxs-lookup"><span data-stu-id="63fbe-119">Passes strings in a structure that is an In parameter.</span></span>|[<span data-ttu-id="63fbe-120">構造体</span><span class="sxs-lookup"><span data-stu-id="63fbe-120">Structs</span></span>](http://msdn.microsoft.com/en-us/96a62265-dcf9-4608-bc0a-1f762ab9f48e)|  
|<span data-ttu-id="63fbe-121">構造体で参照渡し **(char\*)**。</span><span class="sxs-lookup"><span data-stu-id="63fbe-121">In a structure by reference **(char\*)**.</span></span>|<span data-ttu-id="63fbe-122">In/Out パラメーターである構造体で文字列を渡します。</span><span class="sxs-lookup"><span data-stu-id="63fbe-122">Passes strings in a structure that is an In/Out parameter.</span></span> <span data-ttu-id="63fbe-123">アンマネージ関数は文字バッファーへのポインターを必要とし、バッファー サイズは構造体のメンバーです。</span><span class="sxs-lookup"><span data-stu-id="63fbe-123">The unmanaged function expects a pointer to a character buffer and the buffer size is a member of the structure.</span></span>|[<span data-ttu-id="63fbe-124">文字列</span><span class="sxs-lookup"><span data-stu-id="63fbe-124">Strings</span></span>](http://msdn.microsoft.com/en-us/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|<span data-ttu-id="63fbe-125">構造体で参照渡し **(char[])**。</span><span class="sxs-lookup"><span data-stu-id="63fbe-125">In a structure by reference **(char[])**.</span></span>|<span data-ttu-id="63fbe-126">In/Out パラメーターである構造体で文字列を渡します。</span><span class="sxs-lookup"><span data-stu-id="63fbe-126">Passes strings in a structure that is an In/Out parameter.</span></span> <span data-ttu-id="63fbe-127">アンマネージ関数は、埋め込み文字バッファーを必要とします。</span><span class="sxs-lookup"><span data-stu-id="63fbe-127">The unmanaged function expects an embedded character buffer.</span></span>|[<span data-ttu-id="63fbe-128">OSInfo</span><span class="sxs-lookup"><span data-stu-id="63fbe-128">OSInfo</span></span>](http://msdn.microsoft.com/en-us/69d89067-507b-41fe-859d-30bf3ff29455)|  
|<span data-ttu-id="63fbe-129">クラスで値渡し **(char\*)**。</span><span class="sxs-lookup"><span data-stu-id="63fbe-129">In a class by value **(char\*)**.</span></span>|<span data-ttu-id="63fbe-130">クラスで文字列を渡します (クラスは In/Out パラメーターです)。</span><span class="sxs-lookup"><span data-stu-id="63fbe-130">Passes strings in a class (a class is an In/Out parameter).</span></span> <span data-ttu-id="63fbe-131">アンマネージ関数は、文字バッファーへのポインターを必要とします。</span><span class="sxs-lookup"><span data-stu-id="63fbe-131">The unmanaged function expects a pointer to a character buffer.</span></span>|[<span data-ttu-id="63fbe-132">OpenFileDlg</span><span class="sxs-lookup"><span data-stu-id="63fbe-132">OpenFileDlg</span></span>](http://msdn.microsoft.com/en-us/b7dea792-cb92-4baf-ac7b-6a24803e6c75)|  
|<span data-ttu-id="63fbe-133">クラスで値渡し **(char[])**。</span><span class="sxs-lookup"><span data-stu-id="63fbe-133">In a class by value **(char[])**.</span></span>|<span data-ttu-id="63fbe-134">クラスで文字列を渡します (クラスは In/Out パラメーターです)。</span><span class="sxs-lookup"><span data-stu-id="63fbe-134">Passes strings in a class (a class is an In/Out parameter).</span></span> <span data-ttu-id="63fbe-135">アンマネージ関数は、埋め込み文字バッファーを必要とします。</span><span class="sxs-lookup"><span data-stu-id="63fbe-135">The unmanaged function expects an embedded character buffer.</span></span>|[<span data-ttu-id="63fbe-136">OSInfo</span><span class="sxs-lookup"><span data-stu-id="63fbe-136">OSInfo</span></span>](http://msdn.microsoft.com/en-us/69d89067-507b-41fe-859d-30bf3ff29455)|  
|<span data-ttu-id="63fbe-137">文字列の配列として値渡し。</span><span class="sxs-lookup"><span data-stu-id="63fbe-137">As an array of strings by value.</span></span>|<span data-ttu-id="63fbe-138">値によって渡される文字列の配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="63fbe-138">Creates an array of strings that is passed by value.</span></span>|[<span data-ttu-id="63fbe-139">配列</span><span class="sxs-lookup"><span data-stu-id="63fbe-139">Arrays</span></span>](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
|<span data-ttu-id="63fbe-140">文字列を含む構造体の配列として値渡し。</span><span class="sxs-lookup"><span data-stu-id="63fbe-140">As an array of structures that contain strings by value.</span></span>|<span data-ttu-id="63fbe-141">文字列を含む構造体の配列を作成し、配列を値で渡します。</span><span class="sxs-lookup"><span data-stu-id="63fbe-141">Creates an array of structures that contain strings and the array is passed by value.</span></span>|[<span data-ttu-id="63fbe-142">配列</span><span class="sxs-lookup"><span data-stu-id="63fbe-142">Arrays</span></span>](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a><span data-ttu-id="63fbe-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="63fbe-143">See Also</span></span>  
 [<span data-ttu-id="63fbe-144">プラットフォーム呼び出しによるデータのマーシャリング</span><span class="sxs-lookup"><span data-stu-id="63fbe-144">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 [<span data-ttu-id="63fbe-145">プラットフォーム呼び出しのデータ型</span><span class="sxs-lookup"><span data-stu-id="63fbe-145">Platform Invoke Data Types</span></span>](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [<span data-ttu-id="63fbe-146">クラス、構造体、および共用体のマーシャリング</span><span class="sxs-lookup"><span data-stu-id="63fbe-146">Marshaling Classes, Structures, and Unions</span></span>](../../../docs/framework/interop/marshaling-classes-structures-and-unions.md)  
 [<span data-ttu-id="63fbe-147">型の配列のマーシャリング</span><span class="sxs-lookup"><span data-stu-id="63fbe-147">Marshaling Arrays of Types</span></span>](http://msdn.microsoft.com/en-us/049b1c1b-228f-4445-88ec-91bc7fd4b1e8)  
 [<span data-ttu-id="63fbe-148">各種のマーシャリングのサンプル</span><span class="sxs-lookup"><span data-stu-id="63fbe-148">Miscellaneous Marshaling Samples</span></span>](http://msdn.microsoft.com/en-us/a915c948-54e9-4d0f-a525-95a77fd8ed70)
