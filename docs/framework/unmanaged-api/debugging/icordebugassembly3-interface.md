---
title: "ICorDebugAssembly3 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9ed476746e627be987e6307bd367f0d16374de5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="91717-102">ICorDebugAssembly3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="91717-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="91717-103">コンテナー アセンブリとそのコンテナー内のサポートを提供する ICorDebugAssembly インターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="91717-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="91717-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="91717-104">Methods</span></span>  
  
|<span data-ttu-id="91717-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="91717-105">Method</span></span>|<span data-ttu-id="91717-106">説明</span><span class="sxs-lookup"><span data-stu-id="91717-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="91717-107">EnumerateContainedAssemblies メソッド</span><span class="sxs-lookup"><span data-stu-id="91717-107">EnumerateContainedAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="91717-108">このアセンブリに含まれているアセンブリの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="91717-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="91717-109">GetContainerAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="91717-109">GetContainerAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="91717-110">この `ICorDebugAssembly3` オブジェクトのコンテナー アセンブリを返します。</span><span class="sxs-lookup"><span data-stu-id="91717-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91717-111">コメント</span><span class="sxs-lookup"><span data-stu-id="91717-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="91717-112">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="91717-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="91717-113">インターフェイス ポインターを取得するために `QueryInterface` を呼び出そうとすると、.NET ネイティブ外の ICorDebug シナリオに対して `E_NOINTERFACE` が返されます。</span><span class="sxs-lookup"><span data-stu-id="91717-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91717-114">要件</span><span class="sxs-lookup"><span data-stu-id="91717-114">Requirements</span></span>  
 <span data-ttu-id="91717-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="91717-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91717-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91717-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91717-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91717-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91717-118">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91717-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91717-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="91717-119">See Also</span></span>  
 [<span data-ttu-id="91717-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="91717-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="91717-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="91717-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
