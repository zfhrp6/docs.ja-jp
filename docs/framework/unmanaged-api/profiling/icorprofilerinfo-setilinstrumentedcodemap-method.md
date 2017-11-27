---
title: "ICorProfilerInfo::SetILInstrumentedCodeMap メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.SetILInstrumentedCodeMap
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 35c87b98a8e0c02ab6f4bca7a4f7a16ff6839c6b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a><span data-ttu-id="0019f-102">ICorProfilerInfo::SetILInstrumentedCodeMap メソッド</span><span class="sxs-lookup"><span data-stu-id="0019f-102">ICorProfilerInfo::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="0019f-103">指定した Microsoft intermediate language (MSIL) マップ エントリを使用して、指定された関数のコード マップを設定します。</span><span class="sxs-lookup"><span data-stu-id="0019f-103">Sets a code map for the specified function using the specified Microsoft intermediate language (MSIL) map entries.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0019f-104">呼び出し、.NET Framework version 2.0 で`SetILInstrumentedCodeMap`上、`FunctionID`ジェネリックは、特定のアプリケーション ドメインで機能を表しますが、アプリケーション ドメインでは、その関数のすべてのインスタンスに影響することです。</span><span class="sxs-lookup"><span data-stu-id="0019f-104">In the .NET Framework version 2.0, calling `SetILInstrumentedCodeMap` on a `FunctionID` that represents a generic function in a particular application domain will affect all instances of that function in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0019f-105">構文</span><span class="sxs-lookup"><span data-stu-id="0019f-105">Syntax</span></span>  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]  FunctionID functionId,  
    [in]  BOOL       fStartJit,  
    [in]  ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0019f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0019f-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="0019f-107">[in]コード マップを設定する対象の関数の ID。</span><span class="sxs-lookup"><span data-stu-id="0019f-107">[in] The ID of the function for which to set the code map.</span></span>  
  
 `fStartJit`  
 <span data-ttu-id="0019f-108">[in]示すブール値かどうかを呼び出し、`SetILInstrumentedCodeMap`メソッドは、特定の 1 つ目`FunctionID`です。</span><span class="sxs-lookup"><span data-stu-id="0019f-108">[in] A Boolean value that indicates whether the call to the `SetILInstrumentedCodeMap` method is the first for a particular `FunctionID`.</span></span> <span data-ttu-id="0019f-109">設定`fStartJit`に`true`最初の呼び出しで`SetILInstrumentedCodeMap`の指定された`FunctionID`、および`false`以降。</span><span class="sxs-lookup"><span data-stu-id="0019f-109">Set `fStartJit` to `true` in the first call to `SetILInstrumentedCodeMap` for a given `FunctionID`, and to `false` thereafter.</span></span>  
  
 `cILMapEntries`  
 <span data-ttu-id="0019f-110">[in]内の要素の数、`cILMapEntries`配列。</span><span class="sxs-lookup"><span data-stu-id="0019f-110">[in] The number of elements in the `cILMapEntries` array.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="0019f-111">[in]COR_IL_MAP 構造体の配列、それぞれ指定する MSIL のオフセット。</span><span class="sxs-lookup"><span data-stu-id="0019f-111">[in] An array of COR_IL_MAP structures, each of which specifies an MSIL offset.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0019f-112">コメント</span><span class="sxs-lookup"><span data-stu-id="0019f-112">Remarks</span></span>  
 <span data-ttu-id="0019f-113">プロファイラーは、(たとえば、指定されたソース行に達したときに通知する場合など) には、そのメソッドをインストルメント化するために多くの場合、メソッドのソース コード内のステートメントを挿入します。</span><span class="sxs-lookup"><span data-stu-id="0019f-113">A profiler often inserts statements within the source code of a method in order to instrument that method (for example, to notify when a given source line is reached).</span></span> <span data-ttu-id="0019f-114">`SetILInstrumentedCodeMap`プロファイラーは、元の MSIL 命令を新しい場所にマップを有効にします。</span><span class="sxs-lookup"><span data-stu-id="0019f-114">`SetILInstrumentedCodeMap` enables a profiler to map the original MSIL instructions to their new locations.</span></span> <span data-ttu-id="0019f-115">プロファイラーを使用できる、 [icorprofilerinfo::getiltonativemapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)ネイティブ オフセットを指定するため、元の MSIL オフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="0019f-115">A profiler can use the [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) method to get the original MSIL offset for a given native offset.</span></span>  
  
 <span data-ttu-id="0019f-116">デバッガーには、古い各オフセットが MSIL、元の未変更の MSIL コード内でオフセットを指すことと、新しいオフセットが、新しいでインストルメント化されたコード内の MSIL オフセットを指すことが前提としています。</span><span class="sxs-lookup"><span data-stu-id="0019f-116">The debugger will assume that each old offset refers to an MSIL offset within the original, unmodified MSIL code, and that each new offset refers to the MSIL offset within the new, instrumented code.</span></span> <span data-ttu-id="0019f-117">マップは、昇順で並べ替えられます必要があります。</span><span class="sxs-lookup"><span data-stu-id="0019f-117">The map should be sorted in increasing order.</span></span> <span data-ttu-id="0019f-118">正常に動作するステップ実行、次のガイドラインに従ってください。</span><span class="sxs-lookup"><span data-stu-id="0019f-118">For stepping to work properly, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="0019f-119">インストルメント化された MSIL コードを並べ替えないでください。</span><span class="sxs-lookup"><span data-stu-id="0019f-119">Do not reorder instrumented MSIL code.</span></span>  
  
-   <span data-ttu-id="0019f-120">元の MSIL コードを削除しないでください。</span><span class="sxs-lookup"><span data-stu-id="0019f-120">Do not remove the original MSIL code.</span></span>  
  
-   <span data-ttu-id="0019f-121">マップ内のプログラム データベース (PDB) ファイルからのすべてのシーケンス ポイントのエントリを含めます。</span><span class="sxs-lookup"><span data-stu-id="0019f-121">Include entries for all the sequence points from the program database (PDB) file in the map.</span></span> <span data-ttu-id="0019f-122">存在しないエントリを補間、マップは行いません。</span><span class="sxs-lookup"><span data-stu-id="0019f-122">The map does not interpolate missing entries.</span></span> <span data-ttu-id="0019f-123">そのため、次のマップを指定します。</span><span class="sxs-lookup"><span data-stu-id="0019f-123">So, given the following map:</span></span>  
  
     <span data-ttu-id="0019f-124">(新しい 0、0)</span><span class="sxs-lookup"><span data-stu-id="0019f-124">(0 old, 0 new)</span></span>  
  
     <span data-ttu-id="0019f-125">(新しい 5、10)</span><span class="sxs-lookup"><span data-stu-id="0019f-125">(5 old, 10 new)</span></span>  
  
     <span data-ttu-id="0019f-126">(新しい 9、20)</span><span class="sxs-lookup"><span data-stu-id="0019f-126">(9 old, 20 new)</span></span>  
  
    -   <span data-ttu-id="0019f-127">0、1、2、3、または 4 の古いオフセットは、新しいオフセット 0 にマップされます。</span><span class="sxs-lookup"><span data-stu-id="0019f-127">An old offset of 0, 1, 2, 3, or 4 will be mapped to new offset 0.</span></span>  
  
    -   <span data-ttu-id="0019f-128">古いオフセットが 5、6、7、または 8 は、新しいオフセット 10 にマップされます。</span><span class="sxs-lookup"><span data-stu-id="0019f-128">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
    -   <span data-ttu-id="0019f-129">9 以降の古いオフセットは、新しいオフセット 20 にマップされます。</span><span class="sxs-lookup"><span data-stu-id="0019f-129">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
    -   <span data-ttu-id="0019f-130">0、1、2、3、4、5、6、7、8、または 9 の新しいオフセットは、古いオフセット 0 にマップされます。</span><span class="sxs-lookup"><span data-stu-id="0019f-130">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
    -   <span data-ttu-id="0019f-131">10、11、12、13、14、15、16、17、18 または 19 の新しいオフセットは、古いオフセット 5 にマップされます。</span><span class="sxs-lookup"><span data-stu-id="0019f-131">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
    -   <span data-ttu-id="0019f-132">20 以上の新しいオフセットは、古いオフセット 9 にマップされます。</span><span class="sxs-lookup"><span data-stu-id="0019f-132">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0019f-133">要件</span><span class="sxs-lookup"><span data-stu-id="0019f-133">Requirements</span></span>  
 <span data-ttu-id="0019f-134">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0019f-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0019f-135">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0019f-135">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0019f-136">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0019f-136">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0019f-137">**.NET framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0019f-137">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0019f-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="0019f-138">See Also</span></span>  
 [<span data-ttu-id="0019f-139">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0019f-139">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
