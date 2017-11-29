---
title: "ICorDebugGuidToTypeEnum インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGuidToTypeEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGuidToTypeEnum
helpviewer_keywords: ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: aa32b12b-05fc-4ea8-a904-adae25034269
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e419c61d2918a1f17c0739c9782472f25dfe8cfa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="9f87a-102">ICorDebugGuidToTypeEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9f87a-102">ICorDebugGuidToTypeEnum Interface</span></span>
<span data-ttu-id="9f87a-103">Guid のセットおよび ICorDebugType インスタンスによって表されますが、対応する型の間のマッピングを定義する列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="9f87a-103">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="9f87a-104">このインターフェイスは、ICorDebugEnum インターフェイスからメソッドを継承します。</span><span class="sxs-lookup"><span data-stu-id="9f87a-104">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9f87a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="9f87a-105">Methods</span></span>  
  
|<span data-ttu-id="9f87a-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="9f87a-106">Method</span></span>|<span data-ttu-id="9f87a-107">説明</span><span class="sxs-lookup"><span data-stu-id="9f87a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9f87a-108">Icordebugguidtotypeenum::next</span><span class="sxs-lookup"><span data-stu-id="9f87a-108">ICorDebugGuidToTypeEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="9f87a-109">指定した数を取得[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)情報を入力する Guid をマップするインスタンス。</span><span class="sxs-lookup"><span data-stu-id="9f87a-109">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f87a-110">コメント</span><span class="sxs-lookup"><span data-stu-id="9f87a-110">Remarks</span></span>  
 <span data-ttu-id="9f87a-111">`ICorDebugGuidToTypeEnum`インターフェイス オブジェクトを呼び出すことによって取得できる、 [icordebugappdomain 3::getcachedwinrttypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="9f87a-111">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="9f87a-112">デバッガーは、このインターフェイスを呼び出すことができます[次](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)を取得する方法[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)のマッピングを表すオブジェクトの表現を管理する[!INCLUDE[wrt](../../../../includes/wrt-md.md)]に読み込まれた型、呼び出しに使用するアプリケーション ドメイン、 [icordebugappdomain 3::getcachedwinrttypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="9f87a-112">A debugger can call this interface's [Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f87a-113">要件</span><span class="sxs-lookup"><span data-stu-id="9f87a-113">Requirements</span></span>  
 <span data-ttu-id="9f87a-114">**プラットフォーム:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f87a-114">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="9f87a-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f87a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f87a-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f87a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f87a-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f87a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f87a-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="9f87a-118">See Also</span></span>  
 [<span data-ttu-id="9f87a-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="9f87a-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
