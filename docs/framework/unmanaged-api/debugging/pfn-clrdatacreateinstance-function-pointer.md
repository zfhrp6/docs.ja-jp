---
title: "PFN_CLRDataCreateInstance 関数ポインター"
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
- PFN_CLRDataCreateInstance
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- PFN_CLRDataCreateInstance
helpviewer_keywords:
- PFN_CLRDataCreateInstance function pointer [.NET Framework debugging]
ms.assetid: 5c66ac57-d751-4de5-af9f-26ceb949af8b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 98a966434332549d9ceb7f29de81e19fa1b2108f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="pfnclrdatacreateinstance-function-pointer"></a><span data-ttu-id="b25c5-102">PFN_CLRDataCreateInstance 関数ポインター</span><span class="sxs-lookup"><span data-stu-id="b25c5-102">PFN_CLRDataCreateInstance Function Pointer</span></span>
<span data-ttu-id="b25c5-103">指定したターゲット項目のインターフェイス オブジェクトを作成する関数を指します。</span><span class="sxs-lookup"><span data-stu-id="b25c5-103">Points to a function that creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b25c5-104">構文</span><span class="sxs-lookup"><span data-stu-id="b25c5-104">Syntax</span></span>  
  
```  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
    [in]  REFIID           iid,  
    [in]  ICLRDataTarget  *target,  
    [out] void           **iface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b25c5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b25c5-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="b25c5-106">[in]インスタンス化するインターフェイスの識別子。</span><span class="sxs-lookup"><span data-stu-id="b25c5-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="b25c5-107">[in]ユーザー実装へのポインター [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)インターフェイス オブジェクトを作成する対象のターゲット項目を表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="b25c5-107">[in] A pointer to a user-implemented [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="b25c5-108">[out]返されたインターフェイス オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b25c5-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b25c5-109">コメント</span><span class="sxs-lookup"><span data-stu-id="b25c5-109">Remarks</span></span>  
 <span data-ttu-id="b25c5-110">`ICLRDataTarget`オブジェクトは、デバッグ アプリケーションの作成者によって実装されています。</span><span class="sxs-lookup"><span data-stu-id="b25c5-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="b25c5-111">実装は、表されるターゲット項目の種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="b25c5-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="b25c5-112">ターゲット項目には、プロセス、メモリ ダンプ、リモート コンピューター、およびなどがあります。</span><span class="sxs-lookup"><span data-stu-id="b25c5-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b25c5-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="b25c5-113">Requirements</span></span>  
 <span data-ttu-id="b25c5-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b25c5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b25c5-115">**ヘッダー:** ClrData.idl</span><span class="sxs-lookup"><span data-stu-id="b25c5-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="b25c5-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b25c5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b25c5-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b25c5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b25c5-118">参照</span><span class="sxs-lookup"><span data-stu-id="b25c5-118">See Also</span></span>  
 [<span data-ttu-id="b25c5-119">デバッグ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="b25c5-119">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
