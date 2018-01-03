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
ms.workload: dotnet
ms.openlocfilehash: e581b4256da2ecc19a8b97520e0e70fef972b549
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="a45f3-102">ICorDebugAssembly3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a45f3-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="a45f3-103">コンテナー アセンブリとそのコンテナー内のサポートを提供する ICorDebugAssembly インターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="a45f3-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a45f3-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="a45f3-104">Methods</span></span>  
  
|<span data-ttu-id="a45f3-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a45f3-105">Method</span></span>|<span data-ttu-id="a45f3-106">説明</span><span class="sxs-lookup"><span data-stu-id="a45f3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a45f3-107">EnumerateContainedAssemblies メソッド</span><span class="sxs-lookup"><span data-stu-id="a45f3-107">EnumerateContainedAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="a45f3-108">このアセンブリに含まれているアセンブリの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="a45f3-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="a45f3-109">GetContainerAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="a45f3-109">GetContainerAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="a45f3-110">この `ICorDebugAssembly3` オブジェクトのコンテナー アセンブリを返します。</span><span class="sxs-lookup"><span data-stu-id="a45f3-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a45f3-111">コメント</span><span class="sxs-lookup"><span data-stu-id="a45f3-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a45f3-112">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="a45f3-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="a45f3-113">インターフェイス ポインターを取得するために `QueryInterface` を呼び出そうとすると、.NET ネイティブ外の ICorDebug シナリオに対して `E_NOINTERFACE` が返されます。</span><span class="sxs-lookup"><span data-stu-id="a45f3-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a45f3-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="a45f3-114">Requirements</span></span>  
 <span data-ttu-id="a45f3-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a45f3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a45f3-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a45f3-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a45f3-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a45f3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a45f3-118">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a45f3-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a45f3-119">参照</span><span class="sxs-lookup"><span data-stu-id="a45f3-119">See Also</span></span>  
 [<span data-ttu-id="a45f3-120">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a45f3-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="a45f3-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="a45f3-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
