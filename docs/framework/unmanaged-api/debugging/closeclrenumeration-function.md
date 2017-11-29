---
title: "CloseCLREnumeration 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CloseCLREnumeration
api_location: dbgshim.dll
api_type: COM
f1_keywords: CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d9f14b851795c92c3ce0c1e7536a4ff78fbdf927
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="closeclrenumeration-function"></a><span data-ttu-id="056d0-102">CloseCLREnumeration 関数</span><span class="sxs-lookup"><span data-stu-id="056d0-102">CloseCLREnumeration Function</span></span>
<span data-ttu-id="056d0-103">有効な共通言語ランタイム (CLR) 継続スタートアップ イベントによって返されるハンドルの配列内にあるを閉じ、 [EnumerateCLRs 関数](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)、し、ハンドルおよび文字列パス配列のメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="056d0-103">Closes any valid common language runtime (CLR) continue-startup events located in an array of handles returned by the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="056d0-104">構文</span><span class="sxs-lookup"><span data-stu-id="056d0-104">Syntax</span></span>  
  
```  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="056d0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="056d0-105">Parameters</span></span>  
 `pHandleArray`  
 <span data-ttu-id="056d0-106">[in]返されたイベント ハンドルの配列へのポインター、 [EnumerateCLRs 関数](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)です。</span><span class="sxs-lookup"><span data-stu-id="056d0-106">[in] Pointer to the array of event handles returned from the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span></span>  
  
 `pStringArray`  
 <span data-ttu-id="056d0-107">[in]返される CLR 文字列パスの配列へのポインター、 [EnumerateCLRs 関数](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)です。</span><span class="sxs-lookup"><span data-stu-id="056d0-107">[in] Pointer to the array of CLR string paths returned from the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md).</span></span>  
  
 `dwArrayLength`  
 <span data-ttu-id="056d0-108">[in] `pHandleArray` または `pStringArray` (これらは同じです) のサイズ (長さ) を含む DWORD。</span><span class="sxs-lookup"><span data-stu-id="056d0-108">[in] DWORD that contains the size (length) of either `pHandleArray` or `pStringArray` (they are the same).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="056d0-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="056d0-109">Return Value</span></span>  
 <span data-ttu-id="056d0-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="056d0-110">S_OK</span></span>  
 <span data-ttu-id="056d0-111">によって開かれたハンドル、 [EnumerateCLRs 関数](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)が閉じられ、ハンドルおよび文字列配列に割り当てられたメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="056d0-111">Handles opened by the [EnumerateCLRs function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md) are closed, and memory allocated for the handle and string arrays is freed.</span></span>  
  
 <span data-ttu-id="056d0-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="056d0-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="056d0-113">`pHandleArray` の長さが、`dwArrayLength` に渡された長さと一致しません。</span><span class="sxs-lookup"><span data-stu-id="056d0-113">The length of `pHandleArray` does not match the length that is passed in `dwArrayLength`.</span></span>  
  
 <span data-ttu-id="056d0-114">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="056d0-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="056d0-115">`pHandleArray` および `pStringArray` のメモリを解放できません。</span><span class="sxs-lookup"><span data-stu-id="056d0-115">The function is unable to free the memory for `pHandleArray` and `pStringArray`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="056d0-116">要件</span><span class="sxs-lookup"><span data-stu-id="056d0-116">Requirements</span></span>  
 <span data-ttu-id="056d0-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="056d0-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="056d0-118">**ヘッダー:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="056d0-118">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="056d0-119">**ライブラリ:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="056d0-119">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="056d0-120">**.NET framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="056d0-120">**.NET Framework Versions:** 3.5 SP1</span></span>
