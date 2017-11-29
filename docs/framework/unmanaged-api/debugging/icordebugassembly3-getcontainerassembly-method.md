---
title: "ICorDebugAssembly3::GetContainerAssembly メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f9a32520c2a67c0bc51a3f88e9822db49e4a3974
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="88346-102">ICorDebugAssembly3::GetContainerAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="88346-102">ICorDebugAssembly3::GetContainerAssembly Method</span></span>
<span data-ttu-id="88346-103">この `ICorDebugAssembly3` オブジェクトのコンテナー アセンブリを返します。</span><span class="sxs-lookup"><span data-stu-id="88346-103">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88346-104">構文</span><span class="sxs-lookup"><span data-stu-id="88346-104">Syntax</span></span>  
  
```  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="88346-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="88346-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="88346-106">コンテナー アセンブリを表す ICorDebugAssembly オブジェクトのアドレスへのポインターまたは**null**メソッドの呼び出しが失敗した場合。</span><span class="sxs-lookup"><span data-stu-id="88346-106">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88346-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="88346-107">Return Value</span></span>  
 <span data-ttu-id="88346-108">`S_OK`メソッドの呼び出しが成功した場合それ以外の場合、 `S_FALSE`、および`ppAssembly`は**null**です。</span><span class="sxs-lookup"><span data-stu-id="88346-108">`S_OK` if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88346-109">コメント</span><span class="sxs-lookup"><span data-stu-id="88346-109">Remarks</span></span>  
 <span data-ttu-id="88346-110">このアセンブリが 1 つのコンテナー アセンブリ内の他のアセンブリとマージされている場合、このメソッドはコンテナー アセンブリを返します。</span><span class="sxs-lookup"><span data-stu-id="88346-110">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="88346-111">詳細と用語については、次を参照してください。、 [icordebugprocess 6::enablevirtualmodulesplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="88346-111">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88346-112">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="88346-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88346-113">要件</span><span class="sxs-lookup"><span data-stu-id="88346-113">Requirements</span></span>  
 <span data-ttu-id="88346-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="88346-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88346-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="88346-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88346-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88346-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88346-117">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88346-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88346-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="88346-118">See Also</span></span>  
 [<span data-ttu-id="88346-119">ICorDebugAssembly3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="88346-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 [<span data-ttu-id="88346-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="88346-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
