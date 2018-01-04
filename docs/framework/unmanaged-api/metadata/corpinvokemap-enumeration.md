---
title: "CorPinvokeMap 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorPinvokeMap
api_location: mscoree.dll
api_type: COM
f1_keywords: CorPinvokeMap
helpviewer_keywords: CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0e0771ce54e7e2973525bfcf4aba4c1f7ddf0a52
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corpinvokemap-enumeration"></a><span data-ttu-id="3d48c-102">CorPinvokeMap 列挙型</span><span class="sxs-lookup"><span data-stu-id="3d48c-102">CorPinvokeMap Enumeration</span></span>
<span data-ttu-id="3d48c-103">PInvoke 呼び出しのオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="3d48c-103">Specifies options for a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d48c-104">構文</span><span class="sxs-lookup"><span data-stu-id="3d48c-104">Syntax</span></span>  
  
```  
typedef enum  CorPinvokeMap {  
  
    pmNoMangle          = 0x0001,  
  
    pmCharSetMask       = 0x0006,  
    pmCharSetNotSpec    = 0x0000,  
    pmCharSetAnsi       = 0x0002,  
    pmCharSetUnicode    = 0x0004,  
    pmCharSetAuto       = 0x0006,  
  
    pmBestFitUseAssem   = 0x0000,  
    pmBestFitEnabled    = 0x0010,  
    pmBestFitDisabled   = 0x0020,  
    pmBestFitMask       = 0x0030,  
  
    pmThrowOnUnmappableCharUseAssem   = 0x0000,  
    pmThrowOnUnmappableCharEnabled    = 0x1000,  
    pmThrowOnUnmappableCharDisabled   = 0x2000,  
    pmThrowOnUnmappableCharMask       = 0x3000,  
  
    pmSupportsLastError = 0x0040,   
  
    pmCallConvMask      = 0x0700,  
    pmCallConvWinapi    = 0x0100,  
    pmCallConvCdecl     = 0x0200,  
    pmCallConvStdcall   = 0x0300,  
    pmCallConvThiscall  = 0x0400,  
    pmCallConvFastcall  = 0x0500,  
  
    pmMaxValue          = 0xFFFF  
  
} CorPinvokeMap;  
```  
  
## <a name="members"></a><span data-ttu-id="3d48c-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="3d48c-105">Members</span></span>  
  
|<span data-ttu-id="3d48c-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="3d48c-106">Member</span></span>|<span data-ttu-id="3d48c-107">説明</span><span class="sxs-lookup"><span data-stu-id="3d48c-107">Description</span></span>|  
|------------|-----------------|  
|`pmNoMangle`|<span data-ttu-id="3d48c-108">指定された各メンバー名を使用します。</span><span class="sxs-lookup"><span data-stu-id="3d48c-108">Use each member name as specified.</span></span>|  
|`pmCharSetMask`|<span data-ttu-id="3d48c-109">予約済み。</span><span class="sxs-lookup"><span data-stu-id="3d48c-109">Reserved.</span></span>|  
|`pmCharSetNotSpec`|<span data-ttu-id="3d48c-110">予約済み。</span><span class="sxs-lookup"><span data-stu-id="3d48c-110">Reserved.</span></span>|  
|`pmCharSetAnsi`|<span data-ttu-id="3d48c-111">マルチ バイト文字の文字列としての文字列をマーシャ リングします。</span><span class="sxs-lookup"><span data-stu-id="3d48c-111">Marshal strings as multiple-byte character strings.</span></span>|  
|`pmCharSetUnicode`|<span data-ttu-id="3d48c-112">2 バイトの Unicode 文字としての文字列をマーシャ リングします。</span><span class="sxs-lookup"><span data-stu-id="3d48c-112">Marshal strings as Unicode 2-byte characters.</span></span>|  
|`pmCharSetAuto`|<span data-ttu-id="3d48c-113">対象のオペレーティング システムに適した文字列を自動的にマーシャ リングします。</span><span class="sxs-lookup"><span data-stu-id="3d48c-113">Automatically marshal strings appropriately for the target operating system.</span></span> <span data-ttu-id="3d48c-114">既定値は Unicode に Windows NT、Windows 2000、Windows XP および Windows Server 2003 ファミリです。既定値は Windows 98 や Windows me では ANSI</span><span class="sxs-lookup"><span data-stu-id="3d48c-114">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span></span>|  
|`pmBestFitUseAssem`|<span data-ttu-id="3d48c-115">予約済み。</span><span class="sxs-lookup"><span data-stu-id="3d48c-115">Reserved.</span></span>|  
|`pmBestFitEnabled`|<span data-ttu-id="3d48c-116">ANSI 文字セットで一致がない Unicode 文字の最適マッピングを実行します。</span><span class="sxs-lookup"><span data-stu-id="3d48c-116">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span></span>|  
|`pmBestFitDisabled`|<span data-ttu-id="3d48c-117">Unicode 文字の最適マッピングを実行できません。</span><span class="sxs-lookup"><span data-stu-id="3d48c-117">Do not perform best-fit mapping of Unicode characters.</span></span> <span data-ttu-id="3d48c-118">この場合、すべてのマップできない文字に置き換えられます、'?' です。</span><span class="sxs-lookup"><span data-stu-id="3d48c-118">In this case, all unmappable characters will be replaced by a ‘?’.</span></span>|  
|`pmBestFitMask`|<span data-ttu-id="3d48c-119">予約済み。</span><span class="sxs-lookup"><span data-stu-id="3d48c-119">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharUseAssem`|<span data-ttu-id="3d48c-120">予約済み。</span><span class="sxs-lookup"><span data-stu-id="3d48c-120">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharEnabled`|<span data-ttu-id="3d48c-121">相互運用マーシャラーは、マップできない文字を検出したときに、例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="3d48c-121">Throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharDisabled`|<span data-ttu-id="3d48c-122">相互運用マーシャラーは、マップできない文字を検出したときに例外をスローしません。</span><span class="sxs-lookup"><span data-stu-id="3d48c-122">Do not throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharMask`|<span data-ttu-id="3d48c-123">予約されています。</span><span class="sxs-lookup"><span data-stu-id="3d48c-123">Reserved</span></span>|  
|`pmSupportsLastError`|<span data-ttu-id="3d48c-124">呼び出して、Win32、呼び出し先を許可する`SetLastError`属性付きメソッドから戻る前に機能します。</span><span class="sxs-lookup"><span data-stu-id="3d48c-124">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span></span>|  
|`pmCallConvMask`|<span data-ttu-id="3d48c-125">予約されています。</span><span class="sxs-lookup"><span data-stu-id="3d48c-125">Reserved</span></span>|  
|`pmCallConvWinapi`|<span data-ttu-id="3d48c-126">既定のプラットフォーム呼び出し規約を使用します。</span><span class="sxs-lookup"><span data-stu-id="3d48c-126">Use the default platform calling convention.</span></span> <span data-ttu-id="3d48c-127">たとえば、Windows では、既定値は`StdCall`では Windows CE .NET`Cdecl`です。</span><span class="sxs-lookup"><span data-stu-id="3d48c-127">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span></span>|  
|`pmCallConvCdecl`|<span data-ttu-id="3d48c-128">使用して、`Cdecl`呼び出し規約です。</span><span class="sxs-lookup"><span data-stu-id="3d48c-128">Use the `Cdecl` calling convention.</span></span> <span data-ttu-id="3d48c-129">この場合、呼び出し元は、スタックをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="3d48c-129">In this case, the caller cleans the stack.</span></span> <span data-ttu-id="3d48c-130">これにより、関数を呼び出す`varargs`(つまり、可変個のパラメーターを受け入れる関数)。</span><span class="sxs-lookup"><span data-stu-id="3d48c-130">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span></span>|  
|`pmCallConvStdcall`|<span data-ttu-id="3d48c-131">使用して、`StdCall`呼び出し規約です。</span><span class="sxs-lookup"><span data-stu-id="3d48c-131">Use the `StdCall` calling convention.</span></span> <span data-ttu-id="3d48c-132">この場合、呼び出し先がスタックを消去します。</span><span class="sxs-lookup"><span data-stu-id="3d48c-132">In this case, the callee cleans the stack.</span></span> <span data-ttu-id="3d48c-133">これは、アンマネージ関数を呼び出すプラットフォーム呼び出しの既定の規則です。</span><span class="sxs-lookup"><span data-stu-id="3d48c-133">This is the default convention for calling unmanaged functions with platform invoke.</span></span>|  
|`pmCallConvThiscall`|<span data-ttu-id="3d48c-134">使用して、`ThisCall`呼び出し規約です。</span><span class="sxs-lookup"><span data-stu-id="3d48c-134">Use the `ThisCall` calling convention.</span></span> <span data-ttu-id="3d48c-135">この場合、最初のパラメーターは、`this`ポインター レジスタ ECX に保存されます。</span><span class="sxs-lookup"><span data-stu-id="3d48c-135">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span></span> <span data-ttu-id="3d48c-136">その他のパラメーターをスタックにプッシュされます。</span><span class="sxs-lookup"><span data-stu-id="3d48c-136">Other parameters are pushed on the stack.</span></span> <span data-ttu-id="3d48c-137">`ThisCall`呼び出し規約はアンマネージ DLL からエクスポートされたクラスのメソッドの呼び出しに使用します。</span><span class="sxs-lookup"><span data-stu-id="3d48c-137">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span></span>|  
|`pmCallConvFastcall`|<span data-ttu-id="3d48c-138">予約済み。</span><span class="sxs-lookup"><span data-stu-id="3d48c-138">Reserved.</span></span>|  
|`pmMaxValue`|<span data-ttu-id="3d48c-139">予約済み。</span><span class="sxs-lookup"><span data-stu-id="3d48c-139">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3d48c-140">必要条件</span><span class="sxs-lookup"><span data-stu-id="3d48c-140">Requirements</span></span>  
 <span data-ttu-id="3d48c-141">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3d48c-141">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d48c-142">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="3d48c-142">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="3d48c-143">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d48c-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d48c-144">参照</span><span class="sxs-lookup"><span data-stu-id="3d48c-144">See Also</span></span>  
 [<span data-ttu-id="3d48c-145">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="3d48c-145">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
