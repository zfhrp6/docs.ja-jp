---
title: ICorProfilerInfo3::GetStringLayout2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetStringLayout2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetStringLayout2
helpviewer_keywords:
- ICorProfilerInfo3::GetStringLayout2 method [.NET Framework profiling]
- GetStringLayout2 method [.NET Framework profiling]
ms.assetid: 1a268496-ee51-4d84-8700-ee56fd0c499d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57a21a3e4c1324e15a8418dacb8cfe7c5163f334
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454412"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="7d9ab-102">ICorProfilerInfo3::GetStringLayout2 メソッド</span><span class="sxs-lookup"><span data-stu-id="7d9ab-102">ICorProfilerInfo3::GetStringLayout2 Method</span></span>
<span data-ttu-id="7d9ab-103">文字列オブジェクトのレイアウトに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="7d9ab-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="7d9ab-104">このメソッドは、 [icorprofilerinfo 2::getstringlayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="7d9ab-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d9ab-105">構文</span><span class="sxs-lookup"><span data-stu-id="7d9ab-105">Syntax</span></span>  
  
```  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7d9ab-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7d9ab-106">Parameters</span></span>  
 `pStringLengthOffset`  
 <span data-ttu-id="7d9ab-107">[out]相対的に、位置のオフセットへのポインター、`ObjectID`文字列自体の長さを格納するポインター。</span><span class="sxs-lookup"><span data-stu-id="7d9ab-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="7d9ab-108">長さとして格納されている、`DWORD`です。</span><span class="sxs-lookup"><span data-stu-id="7d9ab-108">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="7d9ab-109">[out]相対的に、バッファーのオフセットへのポインター、`ObjectID`ポインターは、ワイド文字の文字列を格納します。</span><span class="sxs-lookup"><span data-stu-id="7d9ab-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d9ab-110">コメント</span><span class="sxs-lookup"><span data-stu-id="7d9ab-110">Remarks</span></span>  
 <span data-ttu-id="7d9ab-111">文字列は、null で終わるができない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7d9ab-111">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d9ab-112">要件</span><span class="sxs-lookup"><span data-stu-id="7d9ab-112">Requirements</span></span>  
 <span data-ttu-id="7d9ab-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7d9ab-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d9ab-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7d9ab-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7d9ab-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d9ab-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d9ab-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d9ab-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d9ab-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="7d9ab-117">See Also</span></span>  
 [<span data-ttu-id="7d9ab-118">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7d9ab-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="7d9ab-119">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="7d9ab-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
