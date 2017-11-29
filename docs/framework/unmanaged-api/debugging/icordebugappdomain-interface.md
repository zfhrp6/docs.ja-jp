---
title: ICorDebugAppDomain Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain
api_location: corguids.lib
api_type: COM
f1_keywords: ICorDebugAppDomain
helpviewer_keywords: ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 19cf38920ed818dfbba9cd83bd64fdc408281e0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomain-interface1"></a><span data-ttu-id="750a4-102">ICorDebugAppDomain Interface1</span><span class="sxs-lookup"><span data-stu-id="750a4-102">ICorDebugAppDomain Interface1</span></span>
<span data-ttu-id="750a4-103">アプリケーション ドメインをデバッグするためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="750a4-103">Provides methods for debugging application domains.</span></span> <span data-ttu-id="750a4-104">このインターフェイスは、ICorDebugController のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="750a4-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="750a4-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="750a4-105">Methods</span></span>  
  
|<span data-ttu-id="750a4-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="750a4-106">Method</span></span>|<span data-ttu-id="750a4-107">説明</span><span class="sxs-lookup"><span data-stu-id="750a4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="750a4-108">Attach メソッド</span><span class="sxs-lookup"><span data-stu-id="750a4-108">Attach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|<span data-ttu-id="750a4-109">アプリケーション ドメインに、デバッガーをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="750a4-109">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="750a4-110">EnumerateAssemblies メソッド</span><span class="sxs-lookup"><span data-stu-id="750a4-110">EnumerateAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="750a4-111">アプリケーション ドメイン内のアセンブリの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="750a4-111">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="750a4-112">EnumerateBreakpoints メソッド</span><span class="sxs-lookup"><span data-stu-id="750a4-112">EnumerateBreakpoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="750a4-113">アプリケーション ドメインですべてのアクティブなブレークポイントの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="750a4-113">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="750a4-114">EnumerateSteppers メソッド</span><span class="sxs-lookup"><span data-stu-id="750a4-114">EnumerateSteppers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="750a4-115">アプリケーション ドメイン内のすべてのアクティブ ステッパの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="750a4-115">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="750a4-116">GetId メソッド</span><span class="sxs-lookup"><span data-stu-id="750a4-116">GetId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|<span data-ttu-id="750a4-117">アプリケーション ドメインの一意の ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="750a4-117">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="750a4-118">GetModuleFromMetaDataInterface メソッド</span><span class="sxs-lookup"><span data-stu-id="750a4-118">GetModuleFromMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="750a4-119">指定されたメタデータ インターフェイス ICorDebugModule オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="750a4-119">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="750a4-120">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="750a4-120">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|<span data-ttu-id="750a4-121">アプリケーション ドメインの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="750a4-121">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="750a4-122">GetObject メソッド</span><span class="sxs-lookup"><span data-stu-id="750a4-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|<span data-ttu-id="750a4-123">共通言語ランタイム (CLR) のアプリケーション ドメインへのインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="750a4-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="750a4-124">GetProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="750a4-124">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|<span data-ttu-id="750a4-125">アプリケーション ドメインを含むプロセスを取得します。</span><span class="sxs-lookup"><span data-stu-id="750a4-125">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="750a4-126">IsAttached メソッド</span><span class="sxs-lookup"><span data-stu-id="750a4-126">IsAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|<span data-ttu-id="750a4-127">アプリケーション ドメインに、デバッガーがアタッチされているかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="750a4-127">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="750a4-128">コメント</span><span class="sxs-lookup"><span data-stu-id="750a4-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="750a4-129">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="750a4-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="750a4-130">要件</span><span class="sxs-lookup"><span data-stu-id="750a4-130">Requirements</span></span>  
 <span data-ttu-id="750a4-131">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="750a4-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="750a4-132">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="750a4-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="750a4-133">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="750a4-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="750a4-134">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="750a4-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="750a4-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="750a4-135">See Also</span></span>  
 [<span data-ttu-id="750a4-136">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="750a4-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
