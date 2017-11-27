---
title: ICorDebugAssembly Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAssembly
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAssembly
helpviewer_keywords: ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 9d657a28-6984-4c5e-8a54-89d20080baff
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d08bb1d2bb7adcbdeb49cd634755d243d34d7f84
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugassembly-interface1"></a><span data-ttu-id="82081-102">ICorDebugAssembly Interface1</span><span class="sxs-lookup"><span data-stu-id="82081-102">ICorDebugAssembly Interface1</span></span>
<span data-ttu-id="82081-103">アセンブリを表します。</span><span class="sxs-lookup"><span data-stu-id="82081-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="82081-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="82081-104">Methods</span></span>  
  
|<span data-ttu-id="82081-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="82081-105">Method</span></span>|<span data-ttu-id="82081-106">説明</span><span class="sxs-lookup"><span data-stu-id="82081-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="82081-107">EnumerateModules メソッド</span><span class="sxs-lookup"><span data-stu-id="82081-107">EnumerateModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="82081-108">アセンブリに含まれるモジュールの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="82081-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="82081-109">GetAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="82081-109">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|<span data-ttu-id="82081-110">インターフェイス ポインターを格納しているアプリケーション ドメインに取得`ICorDebugAssembly`インスタンス。</span><span class="sxs-lookup"><span data-stu-id="82081-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="82081-111">GetCodeBase メソッド</span><span class="sxs-lookup"><span data-stu-id="82081-111">GetCodeBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|<span data-ttu-id="82081-112">.NET Framework の現在のバージョンでは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="82081-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="82081-113">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="82081-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|<span data-ttu-id="82081-114">アセンブリの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="82081-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="82081-115">GetProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="82081-115">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|<span data-ttu-id="82081-116">アセンブリが実行されている ICorDebugProcess インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="82081-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82081-117">コメント</span><span class="sxs-lookup"><span data-stu-id="82081-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82081-118">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="82081-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82081-119">要件</span><span class="sxs-lookup"><span data-stu-id="82081-119">Requirements</span></span>  
 <span data-ttu-id="82081-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="82081-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82081-121">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82081-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82081-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82081-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82081-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82081-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82081-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="82081-124">See Also</span></span>  
 [<span data-ttu-id="82081-125">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="82081-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
