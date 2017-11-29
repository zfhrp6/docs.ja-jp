---
title: "ICorDebugAppDomain3 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain3
helpviewer_keywords: ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 875ef5be-c1e7-4d95-97e9-d3a667aeaba0
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 08f125d7fc388a9b2d31c9cc1cebf2605ffa7e23
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomain3-interface"></a><span data-ttu-id="8cb32-102">ICorDebugAppDomain3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8cb32-102">ICorDebugAppDomain3 Interface</span></span>
<span data-ttu-id="8cb32-103">管理対象の形式に関する情報を取得するメソッドを提供[!INCLUDE[wrt](../../../../includes/wrt-md.md)]アプリケーション ドメインで現在読み込まれている型。</span><span class="sxs-lookup"><span data-stu-id="8cb32-103">Provides methods to retrieve information about the managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types currently loaded in an application domain.</span></span> <span data-ttu-id="8cb32-104">このインターフェイスは、ICorDebugAppDomain および ICorDebugAppDomain2 インターフェイスの拡張です。</span><span class="sxs-lookup"><span data-stu-id="8cb32-104">This interface is an extension of the ICorDebugAppDomain and ICorDebugAppDomain2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8cb32-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="8cb32-105">Methods</span></span>  
  
|<span data-ttu-id="8cb32-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="8cb32-106">Method</span></span>|<span data-ttu-id="8cb32-107">説明</span><span class="sxs-lookup"><span data-stu-id="8cb32-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8cb32-108">Icordebugappdomain 3::getcachedwinrttypes</span><span class="sxs-lookup"><span data-stu-id="8cb32-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|<span data-ttu-id="8cb32-109">キャッシュされたすべての列挙子を取得[!INCLUDE[wrt](../../../../includes/wrt-md.md)]型です。</span><span class="sxs-lookup"><span data-stu-id="8cb32-109">Gets an enumerator for all cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types.</span></span>|  
|[<span data-ttu-id="8cb32-110">Icordebugappdomain 3::getcachedwinrttypesforiids</span><span class="sxs-lookup"><span data-stu-id="8cb32-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|<span data-ttu-id="8cb32-111">キャッシュされた列挙子を取得[!INCLUDE[wrt](../../../../includes/wrt-md.md)]アプリケーション ドメイン内の型、インターフェイスの id に基づいています。</span><span class="sxs-lookup"><span data-stu-id="8cb32-111">Gets an enumerator for cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain based on their interface identifiers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8cb32-112">コメント</span><span class="sxs-lookup"><span data-stu-id="8cb32-112">Remarks</span></span>  
 <span data-ttu-id="8cb32-113">このインターフェイスはデバッガーが関数評価の呼び出しと併用で使用することを意図した`M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`です。</span><span class="sxs-lookup"><span data-stu-id="8cb32-113">This interface is meant to be used by a debugger in conjunction with a function evaluation call to `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span></span> <span data-ttu-id="8cb32-114">メソッドがでサポートされているインターフェイスの id を取得するときに、[!INCLUDE[wrt](../../../../includes/wrt-md.md)]サーバー オブジェクト、デバッガーは、このインターフェイスで定義されているメソッドを使用してこれらのインターフェイスに対応するマネージ型にマップする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8cb32-114">When the method retrieves the interface identifiers supported by a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] server object, the debugger may use the methods defined in this interface to map them to managed types that correspond to those interfaces.</span></span>  
  
 <span data-ttu-id="8cb32-115">このインターフェイスのインスタンスを取得するには実行`QueryInterface`ICorDebugAppDomain または ICorDebugAppDomain2 インターフェイスのインスタンスにします。</span><span class="sxs-lookup"><span data-stu-id="8cb32-115">To retrieve an instance of this interface, run `QueryInterface` on an instance of the ICorDebugAppDomain or ICorDebugAppDomain2 interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8cb32-116">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="8cb32-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cb32-117">要件</span><span class="sxs-lookup"><span data-stu-id="8cb32-117">Requirements</span></span>  
 <span data-ttu-id="8cb32-118">**プラットフォーム:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cb32-118">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="8cb32-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8cb32-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8cb32-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8cb32-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8cb32-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cb32-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cb32-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="8cb32-122">See Also</span></span>  
 [<span data-ttu-id="8cb32-123">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8cb32-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
