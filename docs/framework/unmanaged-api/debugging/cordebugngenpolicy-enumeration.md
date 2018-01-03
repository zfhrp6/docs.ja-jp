---
title: "CorDebugNGenPolicy 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: CorDebugNGenPolicy
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugNGenPolicy
helpviewer_keywords: CorDebugNgenPolicy enumeration [.NET Framework debugging]
ms.assetid: edb4e4d2-3166-44d4-8b17-bf302f7ea093
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 89767da7178319ed1add3dda0620062893487bfd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugngenpolicy-enumeration"></a><span data-ttu-id="2930a-102">CorDebugNGenPolicy 列挙型</span><span class="sxs-lookup"><span data-stu-id="2930a-102">CorDebugNGenPolicy Enumeration</span></span>
<span data-ttu-id="2930a-103">デバッガーがネイティブ イメージ キャッシュからネイティブ (NGen) イメージを読み込むかどうかを指定する値を提供します。</span><span class="sxs-lookup"><span data-stu-id="2930a-103">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2930a-104">構文</span><span class="sxs-lookup"><span data-stu-id="2930a-104">Syntax</span></span>  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="2930a-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="2930a-105">Members</span></span>  
  
|<span data-ttu-id="2930a-106">メンバー名</span><span class="sxs-lookup"><span data-stu-id="2930a-106">Member name</span></span>|<span data-ttu-id="2930a-107">説明</span><span class="sxs-lookup"><span data-stu-id="2930a-107">Description</span></span>|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|<span data-ttu-id="2930a-108">[!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)]アプリ、ローカルのネイティブ イメージ キャッシュからイメージの使用が無効になっています。</span><span class="sxs-lookup"><span data-stu-id="2930a-108">In a [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] app, the use of images from the local native image cache is disabled.</span></span> <span data-ttu-id="2930a-109">デスクトップ アプリでは、この設定には効果がありません。</span><span class="sxs-lookup"><span data-stu-id="2930a-109">In a desktop app, this setting has no effect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2930a-110">コメント</span><span class="sxs-lookup"><span data-stu-id="2930a-110">Remarks</span></span>  
 <span data-ttu-id="2930a-111">`CorDebugNGENPolicy`列挙型を使用して、 [icordebugprocess 5::enablengenpolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="2930a-111">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) method.</span></span> <span data-ttu-id="2930a-112">ローカル ネイティブ イメージ キャッシュからの画像の使用を無効にすると、デバッガーが最適化されたネイティブ イメージではなく、デバッグ可能の JIT コンパイルされたイメージを読み込むことができるようにして、一貫性のあるデバッグ機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="2930a-112">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2930a-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="2930a-113">Requirements</span></span>  
 <span data-ttu-id="2930a-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2930a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2930a-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2930a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2930a-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2930a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2930a-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2930a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2930a-118">参照</span><span class="sxs-lookup"><span data-stu-id="2930a-118">See Also</span></span>  
 [<span data-ttu-id="2930a-119">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="2930a-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
