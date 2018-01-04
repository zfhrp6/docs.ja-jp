---
title: "ICorProfilerInfo2::GetStringLayout メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetStringLayout
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetStringLayout
helpviewer_keywords:
- GetStringLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetStringLayout method [.NET Framework profiling]
ms.assetid: 43189651-a535-4803-a1d1-f1c427ace2ca
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ad91829fab31b47a1dd51bb6cc9118c2ebe4c3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getstringlayout-method"></a><span data-ttu-id="315f7-102">ICorProfilerInfo2::GetStringLayout メソッド</span><span class="sxs-lookup"><span data-stu-id="315f7-102">ICorProfilerInfo2::GetStringLayout Method</span></span>
<span data-ttu-id="315f7-103">文字列オブジェクトのレイアウトに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="315f7-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="315f7-104">このメソッドは非推奨、 [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]、によって置き換えられると、 [icorprofilerinfo 3::getstringlayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="315f7-104">This method is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], and is superseded by the [ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="315f7-105">構文</span><span class="sxs-lookup"><span data-stu-id="315f7-105">Syntax</span></span>  
  
```  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="315f7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="315f7-106">Parameters</span></span>  
 `pBufferLengthOffset`  
 <span data-ttu-id="315f7-107">[out]相対的に、位置のオフセットへのポインター、`ObjectID`ポインターは、文字列の長さを格納します。</span><span class="sxs-lookup"><span data-stu-id="315f7-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span></span> <span data-ttu-id="315f7-108">長さとして格納されている、`DWORD`です。</span><span class="sxs-lookup"><span data-stu-id="315f7-108">The length is stored as a `DWORD`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="315f7-109">このパラメーターは、バッファーの長さではなく、文字列、自体の長さを返します。</span><span class="sxs-lookup"><span data-stu-id="315f7-109">This parameter returns the length of the string itself, not the length of the buffer.</span></span> <span data-ttu-id="315f7-110">バッファーの長さは使用できなくします。</span><span class="sxs-lookup"><span data-stu-id="315f7-110">The length of the buffer is no longer available.</span></span>  
  
 `PStringLengthOffset`  
 <span data-ttu-id="315f7-111">[out]相対的に、位置のオフセットへのポインター、`ObjectID`文字列自体の長さを格納するポインター。</span><span class="sxs-lookup"><span data-stu-id="315f7-111">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="315f7-112">長さとして格納されている、`DWORD`です。</span><span class="sxs-lookup"><span data-stu-id="315f7-112">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="315f7-113">[out]相対的に、バッファーのオフセットへのポインター、`ObjectID`ワイド文字の文字列を格納するポインター。</span><span class="sxs-lookup"><span data-stu-id="315f7-113">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="315f7-114">コメント</span><span class="sxs-lookup"><span data-stu-id="315f7-114">Remarks</span></span>  
 <span data-ttu-id="315f7-115">`GetStringLayout`メソッドは、に対して相対的なオフセットを取得、`ObjectID`ポインターでは、次の格納場所の。</span><span class="sxs-lookup"><span data-stu-id="315f7-115">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span></span>  
  
-   <span data-ttu-id="315f7-116">文字列のバッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="315f7-116">The length of the string's buffer.</span></span>  
  
-   <span data-ttu-id="315f7-117">文字列自体の長さ。</span><span class="sxs-lookup"><span data-stu-id="315f7-117">The length of the string itself.</span></span>  
  
-   <span data-ttu-id="315f7-118">ワイド文字の実際の文字列を格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="315f7-118">The buffer that contains the actual string of wide characters.</span></span>  
  
 <span data-ttu-id="315f7-119">文字列には、null で終わる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="315f7-119">Strings may be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="315f7-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="315f7-120">Requirements</span></span>  
 <span data-ttu-id="315f7-121">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="315f7-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="315f7-122">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="315f7-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="315f7-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="315f7-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="315f7-124">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="315f7-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="315f7-125">参照</span><span class="sxs-lookup"><span data-stu-id="315f7-125">See Also</span></span>  
 [<span data-ttu-id="315f7-126">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="315f7-126">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="315f7-127">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="315f7-127">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
