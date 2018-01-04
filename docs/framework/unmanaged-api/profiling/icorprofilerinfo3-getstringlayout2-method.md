---
title: "ICorProfilerInfo3::GetStringLayout2 メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetStringLayout2 Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetStringLayout2
helpviewer_keywords:
- ICorProfilerInfo3::GetStringLayout2 method [.NET Framework profiling]
- GetStringLayout2 method [.NET Framework profiling]
ms.assetid: 1a268496-ee51-4d84-8700-ee56fd0c499d
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 97f4ab9eefa8bf1f2b3a5057f24b6a940ba91f41
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="aefee-102">ICorProfilerInfo3::GetStringLayout2 メソッド</span><span class="sxs-lookup"><span data-stu-id="aefee-102">ICorProfilerInfo3::GetStringLayout2 Method</span></span>
<span data-ttu-id="aefee-103">文字列オブジェクトのレイアウトに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="aefee-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="aefee-104">このメソッドは、 [icorprofilerinfo 2::getstringlayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="aefee-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aefee-105">構文</span><span class="sxs-lookup"><span data-stu-id="aefee-105">Syntax</span></span>  
  
```  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aefee-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aefee-106">Parameters</span></span>  
 `pStringLengthOffset`  
 <span data-ttu-id="aefee-107">[out]相対的に、位置のオフセットへのポインター、`ObjectID`文字列自体の長さを格納するポインター。</span><span class="sxs-lookup"><span data-stu-id="aefee-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="aefee-108">長さとして格納されている、`DWORD`です。</span><span class="sxs-lookup"><span data-stu-id="aefee-108">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="aefee-109">[out]相対的に、バッファーのオフセットへのポインター、`ObjectID`ポインターは、ワイド文字の文字列を格納します。</span><span class="sxs-lookup"><span data-stu-id="aefee-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aefee-110">コメント</span><span class="sxs-lookup"><span data-stu-id="aefee-110">Remarks</span></span>  
 <span data-ttu-id="aefee-111">文字列は、null で終わるができない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="aefee-111">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aefee-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="aefee-112">Requirements</span></span>  
 <span data-ttu-id="aefee-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="aefee-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aefee-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="aefee-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="aefee-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aefee-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aefee-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aefee-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aefee-117">参照</span><span class="sxs-lookup"><span data-stu-id="aefee-117">See Also</span></span>  
 [<span data-ttu-id="aefee-118">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aefee-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="aefee-119">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="aefee-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
