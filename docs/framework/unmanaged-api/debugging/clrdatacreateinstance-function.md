---
title: "CLRDataCreateInstance 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLRDataCreateInstance
api_location:
- mscordbi.dll
- mscordacwks.dll
api_type: COM
f1_keywords: CLRDataCreateInstance
helpviewer_keywords: CLRDataCreateInstance function [.NET Framework debugging]
ms.assetid: 440bad90-5a88-45e7-9157-4596801d8d19
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c611cc51417199aae7c595e4edd2e9a5360f0f9c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="clrdatacreateinstance-function"></a><span data-ttu-id="a01f0-102">CLRDataCreateInstance 関数</span><span class="sxs-lookup"><span data-stu-id="a01f0-102">CLRDataCreateInstance Function</span></span>
<span data-ttu-id="a01f0-103">指定したターゲット項目のインターフェイス オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="a01f0-103">Creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a01f0-104">構文</span><span class="sxs-lookup"><span data-stu-id="a01f0-104">Syntax</span></span>  
  
```  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,   
    [in]  ICLRDataTarget  *target,   
    [out] void           **iface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a01f0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a01f0-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="a01f0-106">[in]インスタンス化するインターフェイスの識別子。</span><span class="sxs-lookup"><span data-stu-id="a01f0-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="a01f0-107">[in]ユーザー実装へのポインター [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)インターフェイス オブジェクトを作成する対象のターゲット項目を表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a01f0-107">[in] A pointer to a user-implemented [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="a01f0-108">[out]返されたインターフェイス オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a01f0-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a01f0-109">コメント</span><span class="sxs-lookup"><span data-stu-id="a01f0-109">Remarks</span></span>  
 <span data-ttu-id="a01f0-110">`ICLRDataTarget`オブジェクトは、デバッグ アプリケーションの作成者によって実装されています。</span><span class="sxs-lookup"><span data-stu-id="a01f0-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="a01f0-111">実装は、表されるターゲット項目の種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="a01f0-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="a01f0-112">ターゲット項目には、プロセス、メモリ ダンプ、リモート コンピューター、およびなどがあります。</span><span class="sxs-lookup"><span data-stu-id="a01f0-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a01f0-113">要件</span><span class="sxs-lookup"><span data-stu-id="a01f0-113">Requirements</span></span>  
 <span data-ttu-id="a01f0-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a01f0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a01f0-115">**ヘッダー:** ClrData.idl</span><span class="sxs-lookup"><span data-stu-id="a01f0-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="a01f0-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a01f0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a01f0-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a01f0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a01f0-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="a01f0-118">See Also</span></span>  
 [<span data-ttu-id="a01f0-119">デバッグ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="a01f0-119">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
