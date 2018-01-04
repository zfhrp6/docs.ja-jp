---
title: "ICorProfilerInfo::GetILFunctionBody メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetILFunctionBody
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetILFunctionBody
helpviewer_keywords:
- GetILFunctionBody method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBody method [.NET Framework profiling]
ms.assetid: e29b46bc-5fdc-4894-b0c2-619df4b65ded
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 035c2a1926d80b4aaea57523b4ecdd3da6873efe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a><span data-ttu-id="aca37-102">ICorProfilerInfo::GetILFunctionBody メソッド</span><span class="sxs-lookup"><span data-stu-id="aca37-102">ICorProfilerInfo::GetILFunctionBody Method</span></span>
<span data-ttu-id="aca37-103">開始位置のヘッダーとして、Microsoft intermediate language (MSIL) コードでメソッドの本体へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="aca37-103">Gets a pointer to the body of a method in Microsoft intermediate language (MSIL) code, starting at its header.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aca37-104">構文</span><span class="sxs-lookup"><span data-stu-id="aca37-104">Syntax</span></span>  
  
```  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aca37-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aca37-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="aca37-106">[in]関数が存在するモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="aca37-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodId`  
 <span data-ttu-id="aca37-107">[in]メソッドのメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="aca37-107">[in] The metadata token for the method.</span></span>  
  
 `ppMethodHeader`  
 <span data-ttu-id="aca37-108">[out]メソッドのヘッダーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aca37-108">[out] A pointer to the method's header.</span></span>  
  
 `pcbMethodSize`  
 <span data-ttu-id="aca37-109">[out]メソッドのサイズを指定する整数。</span><span class="sxs-lookup"><span data-stu-id="aca37-109">[out] An integer that specifies the size of the method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aca37-110">コメント</span><span class="sxs-lookup"><span data-stu-id="aca37-110">Remarks</span></span>  
 <span data-ttu-id="aca37-111">メソッドは、中で、モジュールによって制限されます。</span><span class="sxs-lookup"><span data-stu-id="aca37-111">A method is scoped by the module in which it lives.</span></span> <span data-ttu-id="aca37-112">`GetILFunctionBody`メソッドが共通言語ランタイム (CLR) によって読み込まれた前に、MSIL コードにツールへのアクセスを提供するように設計で、目的のインスタンスを検索するメソッドのメタデータ トークンを使用しています。</span><span class="sxs-lookup"><span data-stu-id="aca37-112">Because the `GetILFunctionBody` method is designed to give a tool access to the MSIL code before it has been loaded by the common language runtime (CLR), it uses the metadata token of the method to find the desired instance.</span></span>  
  
 <span data-ttu-id="aca37-113">`GetILFunctionBody`CORPROF_E_FUNCTION_NOT_IL HRESULT を返す場合、`methodId`任意の MSIL コード (など、抽象メソッドまたはプラットフォームは、(PInvoke) メソッドを呼び出す) ことがなく、メソッドを指します。</span><span class="sxs-lookup"><span data-stu-id="aca37-113">`GetILFunctionBody` can return a CORPROF_E_FUNCTION_NOT_IL HRESULT if the `methodId` points to a method without any MSIL code (such as an abstract method, or a platform invoke (PInvoke) method).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aca37-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="aca37-114">Requirements</span></span>  
 <span data-ttu-id="aca37-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="aca37-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aca37-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="aca37-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="aca37-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aca37-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aca37-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aca37-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aca37-119">参照</span><span class="sxs-lookup"><span data-stu-id="aca37-119">See Also</span></span>  
 [<span data-ttu-id="aca37-120">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aca37-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
