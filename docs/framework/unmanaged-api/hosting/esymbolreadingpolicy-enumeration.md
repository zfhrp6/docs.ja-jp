---
title: "ESymbolReadingPolicy 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ESymbolReadingPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ESymbolReadingPolicy
helpviewer_keywords: ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4fdb18a343f91e85619f6d62e466fdd558044727
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="f273e-102">ESymbolReadingPolicy 列挙型</span><span class="sxs-lookup"><span data-stu-id="f273e-102">ESymbolReadingPolicy Enumeration</span></span>
<span data-ttu-id="f273e-103">プログラム データベース (PDB) ファイルを読み取るためのポリシー設定の値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f273e-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f273e-104">構文</span><span class="sxs-lookup"><span data-stu-id="f273e-104">Syntax</span></span>  
  
```  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="f273e-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="f273e-105">Members</span></span>  
  
|<span data-ttu-id="f273e-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="f273e-106">Member</span></span>|<span data-ttu-id="f273e-107">説明</span><span class="sxs-lookup"><span data-stu-id="f273e-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="f273e-108">デバッガーが常に PDB ファイルを読み取ることを指定します。</span><span class="sxs-lookup"><span data-stu-id="f273e-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="f273e-109">デバッガーが完全に信頼されたアセンブリに関連付けられている PDB ファイルのみを読み取ることを指定します。</span><span class="sxs-lookup"><span data-stu-id="f273e-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="f273e-110">デバッガーが PDB ファイルを読み取る必要がありますしないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="f273e-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f273e-111">コメント</span><span class="sxs-lookup"><span data-stu-id="f273e-111">Remarks</span></span>  
 <span data-ttu-id="f273e-112">`ESymbolReadingPolicy`と列挙が使用される、 [iclrdebugmanager::setsymbolreadingpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="f273e-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f273e-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="f273e-113">Requirements</span></span>  
 <span data-ttu-id="f273e-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f273e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f273e-115">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f273e-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f273e-116">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f273e-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f273e-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f273e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f273e-118">参照</span><span class="sxs-lookup"><span data-stu-id="f273e-118">See Also</span></span>  
 [<span data-ttu-id="f273e-119">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="f273e-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
