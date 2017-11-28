---
title: "ICorDebugDataTarget2::GetImageFromPointer メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e56f65aea12c71145c99a9a195b910ef2876aa09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="0d095-102">ICorDebugDataTarget2::GetImageFromPointer メソッド</span><span class="sxs-lookup"><span data-stu-id="0d095-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="0d095-103">モジュールのアドレスから、そのモジュールのベース アドレスとサイズを返します。</span><span class="sxs-lookup"><span data-stu-id="0d095-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d095-104">構文</span><span class="sxs-lookup"><span data-stu-id="0d095-104">Syntax</span></span>  
  
```  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,   
   [out] CORDB_ADDRESS *pImageBase,   
   [out] ULONG32 *pSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0d095-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0d095-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="0d095-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)モジュール内のアドレスを表す値です。</span><span class="sxs-lookup"><span data-stu-id="0d095-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="0d095-107">[out]A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)モジュールのベース アドレスを表す値です。</span><span class="sxs-lookup"><span data-stu-id="0d095-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="0d095-108">モジュールのサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0d095-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d095-109">コメント</span><span class="sxs-lookup"><span data-stu-id="0d095-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d095-110">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="0d095-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d095-111">要件</span><span class="sxs-lookup"><span data-stu-id="0d095-111">Requirements</span></span>  
 <span data-ttu-id="0d095-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0d095-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d095-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0d095-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d095-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d095-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d095-115">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d095-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d095-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="0d095-116">See Also</span></span>  
 [<span data-ttu-id="0d095-117">ICorDebugDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0d095-117">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="0d095-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="0d095-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
