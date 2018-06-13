---
title: ICorProfilerInfo7::GetInMemorySymbolsLength メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e662270fc8db3fb85e058e8d4f3346f58f79bb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457962"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a><span data-ttu-id="1920b-102">ICorProfilerInfo7::GetInMemorySymbolsLength メソッド</span><span class="sxs-lookup"><span data-stu-id="1920b-102">ICorProfilerInfo7::GetInMemorySymbolsLength Method</span></span>
<span data-ttu-id="1920b-103">[.NET Framework 4.6.1 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="1920b-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="1920b-104">メモリ内のシンボルのストリームの長さを返します。</span><span class="sxs-lookup"><span data-stu-id="1920b-104">Returns the length of an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1920b-105">構文</span><span class="sxs-lookup"><span data-stu-id="1920b-105">Syntax</span></span>  
  
```  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1920b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1920b-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="1920b-107">[in]メモリ内ストリームを含むモジュールの識別子。</span><span class="sxs-lookup"><span data-stu-id="1920b-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 <span data-ttu-id="1920b-108">pCountSymbolBytes</span><span class="sxs-lookup"><span data-stu-id="1920b-108">pCountSymbolBytes</span></span>  
 <span data-ttu-id="1920b-109">[out]ポインター、`DWORD`値をメソッドが戻るときに、バイト単位のストリームの長さが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1920b-109">[out] A pointer to a `DWORD` value that, when the method returns, contains the length of the stream in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1920b-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="1920b-110">Return Value</span></span>  
 <span data-ttu-id="1920b-111">このメソッドを返します`S_OK`かどうか、メモリ ストリームの長さを決定する場合でも、ゼロ (0) であります。</span><span class="sxs-lookup"><span data-stu-id="1920b-111">The method returns `S_OK` if the length of the memory stream can be determined, even if it is zero (0).</span></span>  
  
 <span data-ttu-id="1920b-112">このメソッドを返します`CORPROF_E_MODULE_IS_DYNAMIC`を使用して、メソッドが作成された場合<xref:System.Reflection.Emit?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="1920b-112">The method returns `CORPROF_E_MODULE_IS_DYNAMIC` if the method was created using <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1920b-113">コメント</span><span class="sxs-lookup"><span data-stu-id="1920b-113">Remarks</span></span>  
 <span data-ttu-id="1920b-114">モジュールは、メモリ内のシンボルには場合、に、ストリームの長さが格納されます。`pCountSymbolBytes`です。</span><span class="sxs-lookup"><span data-stu-id="1920b-114">If the module has in-memory symbols, the length of the stream is placed in `pCountSymbolBytes`.</span></span> <span data-ttu-id="1920b-115">モジュールは、メモリ内のシンボルを持っていない場合`*pCountSymbolBytes = 0`です。</span><span class="sxs-lookup"><span data-stu-id="1920b-115">If the module doesn't have in-memory     symbols, `*pCountSymbolBytes = 0`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1920b-116">現在の実装は、Reflection.Emit をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="1920b-116">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="1920b-117">メソッドを返しますのかどうか、モジュールは、Reflection.Emit を使用して作成された、`CORPROF_E_MODULE_IS_DYNAMIC`です。</span><span class="sxs-lookup"><span data-stu-id="1920b-117">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1920b-118">要件</span><span class="sxs-lookup"><span data-stu-id="1920b-118">Requirements</span></span>  
 <span data-ttu-id="1920b-119">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1920b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1920b-120">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1920b-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1920b-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1920b-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1920b-122">**.NET Framework のバージョン:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1920b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1920b-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="1920b-123">See Also</span></span>  
 [<span data-ttu-id="1920b-124">ICorProfilerInfo7 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1920b-124">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
