---
title: "StrongNameFreeBuffer 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- StrongNameFreeBuffer
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer function [.NET Framework strong naming]
ms.assetid: eda21ecf-4734-4f92-aaba-9f34884385db
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f4f5bde035b0ab9df07bb0ab709a67ae1a4cff3f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="33c71-102">StrongNameFreeBuffer 関数</span><span class="sxs-lookup"><span data-stu-id="33c71-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="33c71-103">など、厳密な名前の関数を前回呼び出したときに割り当てられたメモリを解放[StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)、 [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md)、または[StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="33c71-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="33c71-104">この関数は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="33c71-104">This function has been deprecated.</span></span> <span data-ttu-id="33c71-105">使用して、 [iclrstrongname::strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="33c71-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33c71-106">構文</span><span class="sxs-lookup"><span data-stu-id="33c71-106">Syntax</span></span>  
  
```  
VOID StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="33c71-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="33c71-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="33c71-108">[in]解放するメモリへのポインター。</span><span class="sxs-lookup"><span data-stu-id="33c71-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33c71-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="33c71-109">Requirements</span></span>  
 <span data-ttu-id="33c71-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="33c71-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33c71-111">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="33c71-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="33c71-112">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="33c71-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="33c71-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33c71-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33c71-114">参照</span><span class="sxs-lookup"><span data-stu-id="33c71-114">See Also</span></span>  
 [<span data-ttu-id="33c71-115">StrongNameFreeBuffer メソッド</span><span class="sxs-lookup"><span data-stu-id="33c71-115">StrongNameFreeBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)  
 [<span data-ttu-id="33c71-116">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="33c71-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
