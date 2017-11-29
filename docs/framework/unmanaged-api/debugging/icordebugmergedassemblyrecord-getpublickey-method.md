---
title: "ICorDebugMergedAssemblyRecord::GetPublicKey メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7d379f0df70690501920a9ba5b40d560b10a7cb7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="32f34-102">ICorDebugMergedAssemblyRecord::GetPublicKey メソッド</span><span class="sxs-lookup"><span data-stu-id="32f34-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="32f34-103">アセンブリの公開キーを取得します。</span><span class="sxs-lookup"><span data-stu-id="32f34-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32f34-104">構文</span><span class="sxs-lookup"><span data-stu-id="32f34-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32f34-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="32f34-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="32f34-106">[in] `pbPublicKey` 配列の最大バイト数。</span><span class="sxs-lookup"><span data-stu-id="32f34-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="32f34-107">[out] `pbPublicKey` 配列への実際の書き込みバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="32f34-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="32f34-108">[out] アセンブリの公開キーを含むバイト配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="32f34-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32f34-109">コメント</span><span class="sxs-lookup"><span data-stu-id="32f34-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32f34-110">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="32f34-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32f34-111">要件</span><span class="sxs-lookup"><span data-stu-id="32f34-111">Requirements</span></span>  
 <span data-ttu-id="32f34-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="32f34-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32f34-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="32f34-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32f34-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32f34-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32f34-115">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32f34-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32f34-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="32f34-116">See Also</span></span>  
 [<span data-ttu-id="32f34-117">ICorDebugMergedAssemblyRecord インターフェイス</span><span class="sxs-lookup"><span data-stu-id="32f34-117">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="32f34-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="32f34-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
