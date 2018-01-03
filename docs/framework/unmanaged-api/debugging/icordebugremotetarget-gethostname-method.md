---
title: "ICorDebugRemoteTarget::GetHostName メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRemoteTarget.GetHostName
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugRemoteTarget::GetHostName
helpviewer_keywords:
- ICorDebugRemoteTarget::GetHostName method [.NET Framework debugging]
- GetHostName method, ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: 1c7276f7-7e54-470c-808c-e13745ac07a1
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 45fa4afebda00cb2549a5c18ba81c6bb4e8210e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugremotetargetgethostname-method"></a><span data-ttu-id="49c66-102">ICorDebugRemoteTarget::GetHostName メソッド</span><span class="sxs-lookup"><span data-stu-id="49c66-102">ICorDebugRemoteTarget::GetHostName Method</span></span>
<span data-ttu-id="49c66-103">リモート デバッグ対象コンピューターの完全修飾ドメイン名または IPv4 アドレスを返します。</span><span class="sxs-lookup"><span data-stu-id="49c66-103">Returns the fully qualified domain name or IPv4 address of the remote debugging target machine.</span></span> <span data-ttu-id="49c66-104">IPV6 はこの時点ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="49c66-104">IPV6 is not supported at this time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49c66-105">構文</span><span class="sxs-lookup"><span data-stu-id="49c66-105">Syntax</span></span>  
  
```  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="49c66-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="49c66-106">Parameters</span></span>  
 `cchHostName`  
 <span data-ttu-id="49c66-107">[入力] `szHostName` バッファーのサイズ (文字単位)。</span><span class="sxs-lookup"><span data-stu-id="49c66-107">[in] The size, in characters, of the `szHostName` buffer.</span></span> <span data-ttu-id="49c66-108">このパラメーターが 0 である場合、`szHostName` は null であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="49c66-108">If this parameter is 0 (zero), `szHostName` must be null.</span></span>  
  
 `pcchHostName`  
 <span data-ttu-id="49c66-109">[出力] 配列に返される文字数。ホスト名または IP アドレスの null 終端文字を含みます。</span><span class="sxs-lookup"><span data-stu-id="49c66-109">[out] The number of characters, including a null terminator, in the host name or IP address.</span></span> <span data-ttu-id="49c66-110">このパラメーターには、null を指定できます。</span><span class="sxs-lookup"><span data-stu-id="49c66-110">This parameter can be null.</span></span>  
  
 `szHostName`  
 <span data-ttu-id="49c66-111">[出力] ホスト名または IP アドレスを含むバッファー。</span><span class="sxs-lookup"><span data-stu-id="49c66-111">[out] Buffer that contains the host name or IP address.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49c66-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="49c66-112">Return Value</span></span>  
 <span data-ttu-id="49c66-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="49c66-113">S_OK</span></span>  
 <span data-ttu-id="49c66-114">ホスト名または IP アドレスは正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="49c66-114">The host name or IP address was successfully returned.</span></span>  
  
 <span data-ttu-id="49c66-115">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="49c66-115">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="49c66-116">ホスト名または IP アドレスを返すことができません。</span><span class="sxs-lookup"><span data-stu-id="49c66-116">Unable to return the host name or IP address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49c66-117">コメント</span><span class="sxs-lookup"><span data-stu-id="49c66-117">Remarks</span></span>  
 <span data-ttu-id="49c66-118">このメソッドは、デバッガー ライターによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="49c66-118">This method is implemented by the debugger writer.</span></span> <span data-ttu-id="49c66-119">複数の呼び出しパラダイムに従う必要があります。最初の呼び出しでは、呼び出し元が `cchHostName` および `szHostName` の両方に null を渡し、`pcchHostName` が必要なバッファーのサイズを返します。</span><span class="sxs-lookup"><span data-stu-id="49c66-119">It must follow the multiple call paradigm: On the first call, the caller passes null to both `cchHostName` and `szHostName`, and `pcchHostName` returns the size of the required buffer .</span></span> <span data-ttu-id="49c66-120">第 2 の呼び出しでは、以前に返されたサイズが `cchHostName` に渡され、適切にサイズ設定されたバッファーが `szHostName` に渡されます。</span><span class="sxs-lookup"><span data-stu-id="49c66-120">On the second call, the size that was previously returned is passed in `cchHostName`, and an appropriately sized buffer is passed in `szHostName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49c66-121">必要条件</span><span class="sxs-lookup"><span data-stu-id="49c66-121">Requirements</span></span>  
 <span data-ttu-id="49c66-122">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="49c66-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49c66-123">**ヘッダー:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="49c66-123">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="49c66-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49c66-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49c66-125">**.NET framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="49c66-125">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49c66-126">参照</span><span class="sxs-lookup"><span data-stu-id="49c66-126">See Also</span></span>  
 [<span data-ttu-id="49c66-127">ICorDebugRemoteTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="49c66-127">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="49c66-128">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="49c66-128">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
