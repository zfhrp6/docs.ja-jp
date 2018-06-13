---
title: ICorDebugMergedAssemblyRecord::GetPublicKeyToken メソッド
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71b70118d77deb7ad6879ed4bd48b1cd37122820
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414009"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a><span data-ttu-id="e337b-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken メソッド</span><span class="sxs-lookup"><span data-stu-id="e337b-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken Method</span></span>
<span data-ttu-id="e337b-103">アセンブリの公開キー トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="e337b-103">Gets the assembly's public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e337b-104">構文</span><span class="sxs-lookup"><span data-stu-id="e337b-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,   
   [out] ULONG32 *pcbPublicKeyToken,   
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e337b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e337b-105">Parameters</span></span>  
 `cbPublicKeyToken`  
 <span data-ttu-id="e337b-106">[in] `pbPublicKeyToken` 配列の最大バイト数。</span><span class="sxs-lookup"><span data-stu-id="e337b-106">[in] The maximum number of bytes in the `pbPublicKeyToken` array.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="e337b-107">[out] `pbPublicKeyToken` 配列への実際の書き込みバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e337b-107">[out] A pointer to the actual number of bytes written to the `pbPublicKeyToken` array.</span></span>  
  
 `pbPublicKeyToken`  
 <span data-ttu-id="e337b-108">[out] アセンブリの公開キー トークンを含むバイト配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e337b-108">[out] A pointer to a byte array that contains the assembly's public key token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e337b-109">コメント</span><span class="sxs-lookup"><span data-stu-id="e337b-109">Remarks</span></span>  
 <span data-ttu-id="e337b-110">アセンブリの公開キー トークンは、その公開キーの SHA1 ハッシュの最後の 8 バイトです。</span><span class="sxs-lookup"><span data-stu-id="e337b-110">An assembly's public key token is the last eight bytes of a SHA1 hash of its public key.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e337b-111">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="e337b-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e337b-112">要件</span><span class="sxs-lookup"><span data-stu-id="e337b-112">Requirements</span></span>  
 <span data-ttu-id="e337b-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e337b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e337b-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e337b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e337b-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e337b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e337b-116">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e337b-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e337b-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="e337b-117">See Also</span></span>  
 [<span data-ttu-id="e337b-118">ICorDebugMergedAssemblyRecord インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e337b-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="e337b-119">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e337b-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
