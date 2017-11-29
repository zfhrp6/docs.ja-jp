---
title: "ICorProfilerInfo3::GetRuntimeInformation メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetRuntimeInformation Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a18f0604b1585ffb1dd8230c289bcd95bfa3dfae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a><span data-ttu-id="fb01d-102">ICorProfilerInfo3::GetRuntimeInformation メソッド</span><span class="sxs-lookup"><span data-stu-id="fb01d-102">ICorProfilerInfo3::GetRuntimeInformation Method</span></span>
<span data-ttu-id="fb01d-103">プロファイリングされている共通言語ランタイム (CLR) のバージョン情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="fb01d-103">Provides version information about the common language runtime (CLR) that is being profiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb01d-104">構文</span><span class="sxs-lookup"><span data-stu-id="fb01d-104">Syntax</span></span>  
  
```  
HRESULT GetRuntimeInformation(  
       [out] USHORT *pClrInstanceId,  
       [out] COR_PRF_RUNTIME_TYPE *pRuntimeType,  
       [out] USHORT *pMajorVersion,  
       [out] USHORT *pMinorVersion,  
       [out] USHORT *pBuildNumber,  
       [out] USHORT *pQFEVersion,  
       [in]  ULONG  cchVersionString,  
       [out] ULONG  *pcchVersionString,  
       [out, size_is(cchVersionString), length_is(*pcchVersionString)]  
                   WCHAR  szVersionString[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb01d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fb01d-105">Parameters</span></span>  
 `pClrInstanceId`  
 <span data-ttu-id="fb01d-106">[out]プロセスで実行中の CLR インスタンスの代表者の ID です。</span><span class="sxs-lookup"><span data-stu-id="fb01d-106">[out] The representative ID of a running CLR instance in a process.</span></span> <span data-ttu-id="fb01d-107">これと同じ、 `ClrInstanceID` Windows (ETW) のスタートアップ イベントのイベントのトレースをレポートすることです。</span><span class="sxs-lookup"><span data-stu-id="fb01d-107">This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.</span></span>  
  
 `pRuntimeType`  
 <span data-ttu-id="fb01d-108">[out]ランタイムの型。</span><span class="sxs-lookup"><span data-stu-id="fb01d-108">[out] The runtime type.</span></span> <span data-ttu-id="fb01d-109">このパラメーターを返します`COR_PRF_DESKTOP_CLR`、CLR のデスクトップ バージョンのまたは`COR_PRF_CORE_CLR`Silverlight で使用されている CLR のコア バージョン。</span><span class="sxs-lookup"><span data-stu-id="fb01d-109">This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.</span></span>  
  
 `pMajorVersion`  
 <span data-ttu-id="fb01d-110">[out]CLR のメジャー バージョン番号。</span><span class="sxs-lookup"><span data-stu-id="fb01d-110">[out] The major version number of the CLR.</span></span>  
  
 `pMinorVersion`  
 <span data-ttu-id="fb01d-111">[out]CLR のマイナー バージョン番号。</span><span class="sxs-lookup"><span data-stu-id="fb01d-111">[out] The minor version number of the CLR.</span></span>  
  
 `pBuildVersion`  
 <span data-ttu-id="fb01d-112">[out]CLR のビルド バージョン番号。</span><span class="sxs-lookup"><span data-stu-id="fb01d-112">[out] The build version number of the CLR.</span></span>  
  
 `pQFEVersion`  
 <span data-ttu-id="fb01d-113">[out]ソフトウェア更新プログラムに関連付けられている CLR のバージョン番号。</span><span class="sxs-lookup"><span data-stu-id="fb01d-113">[out] The version number of the CLR that is associated with a software update.</span></span>  
  
 `cchVersionString`  
 <span data-ttu-id="fb01d-114">[in]バッファーの文字の長さを`szVersionString`を指します。</span><span class="sxs-lookup"><span data-stu-id="fb01d-114">[in] The length, in characters, of the buffer that `szVersionString` points to.</span></span>  
  
 `pcchVersionString`  
 <span data-ttu-id="fb01d-115">[out]文字の長さの`szVersionString`します。</span><span class="sxs-lookup"><span data-stu-id="fb01d-115">[out] The length, in characters, of `szVersionString`.</span></span>  
  
 `szVersionString`  
 <span data-ttu-id="fb01d-116">[out]CLR バージョン文字列です。</span><span class="sxs-lookup"><span data-stu-id="fb01d-116">[out] The CLR version string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb01d-117">コメント</span><span class="sxs-lookup"><span data-stu-id="fb01d-117">Remarks</span></span>  
 <span data-ttu-id="fb01d-118">任意のパラメーターに null を渡すことがあります。</span><span class="sxs-lookup"><span data-stu-id="fb01d-118">You may pass null for any parameter.</span></span> <span data-ttu-id="fb01d-119">ただし、 `pcchVersionString` null にすることはできませんしない限り、`szVersionString`も null です。</span><span class="sxs-lookup"><span data-stu-id="fb01d-119">However, `pcchVersionString` cannot be null unless `szVersionString` is also null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb01d-120">要件</span><span class="sxs-lookup"><span data-stu-id="fb01d-120">Requirements</span></span>  
 <span data-ttu-id="fb01d-121">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fb01d-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb01d-122">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fb01d-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fb01d-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb01d-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb01d-124">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb01d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb01d-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="fb01d-125">See Also</span></span>  
 [<span data-ttu-id="fb01d-126">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fb01d-126">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="fb01d-127">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="fb01d-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="fb01d-128">プロファイル</span><span class="sxs-lookup"><span data-stu-id="fb01d-128">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
