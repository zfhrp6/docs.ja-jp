---
title: "ECustomDumpFlavor 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ECustomDumpFlavor
api_location: mscoree.dll
api_type: COM
f1_keywords: ECustomDumpFlavor
helpviewer_keywords: ECustomDumpFlavor enumeration [.NET Framework hosting]
ms.assetid: b39b3320-fac7-41f1-9a03-ab6fb0cd89c7
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a7317a3a12acef2a16deebab9a1e1b10205ebf6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ecustomdumpflavor-enumeration"></a><span data-ttu-id="9ec9f-102">ECustomDumpFlavor 列挙型</span><span class="sxs-lookup"><span data-stu-id="9ec9f-102">ECustomDumpFlavor Enumeration</span></span>
<span data-ttu-id="9ec9f-103">エラーを報告するときに、ヒープのカスタムのサブセットに含めるには、どの項目がダンプを示す値を含みます。</span><span class="sxs-lookup"><span data-stu-id="9ec9f-103">Contains values that indicate which items to include in a custom subset of a heap dump when reporting errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ec9f-104">構文</span><span class="sxs-lookup"><span data-stu-id="9ec9f-104">Syntax</span></span>  
  
```  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a><span data-ttu-id="9ec9f-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="9ec9f-105">Members</span></span>  
  
|<span data-ttu-id="9ec9f-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="9ec9f-106">Member</span></span>|<span data-ttu-id="9ec9f-107">説明</span><span class="sxs-lookup"><span data-stu-id="9ec9f-107">Description</span></span>|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|<span data-ttu-id="9ec9f-108">カスタム ヒープ ダンプする必要があります、ミニダンプとして起動し、いずれかで指定された追加のデータを含めることを示す[CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)インスタンスが同じメソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="9ec9f-108">Specifies that the custom heap dump should start as a minidump and include extra data specified by any [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances passed to the same method.</span></span>|  
|`DUMP_FLAVOR_NonHeapCLRState`|<span data-ttu-id="9ec9f-109">カスタム ヒープ ダンプが動的に割り当てられていないすべての実行時の状態データを収集する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="9ec9f-109">Specifies that the custom heap dump should gather all run-time state data that was not dynamically allocated.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ec9f-110">コメント</span><span class="sxs-lookup"><span data-stu-id="9ec9f-110">Remarks</span></span>  
 <span data-ttu-id="9ec9f-111">型のパラメーター`ECustomDumpFlavor`に渡される、 [iclrerrorreportingmanager::begincustomdump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="9ec9f-111">A parameter of type `ECustomDumpFlavor` is passed to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ec9f-112">要件</span><span class="sxs-lookup"><span data-stu-id="9ec9f-112">Requirements</span></span>  
 <span data-ttu-id="9ec9f-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9ec9f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ec9f-114">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9ec9f-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9ec9f-115">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9ec9f-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ec9f-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ec9f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ec9f-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ec9f-117">See Also</span></span>  
 [<span data-ttu-id="9ec9f-118">ECustomDumpItemKind 列挙型</span><span class="sxs-lookup"><span data-stu-id="9ec9f-118">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)  
 [<span data-ttu-id="9ec9f-119">ICLRErrorReportingManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ec9f-119">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [<span data-ttu-id="9ec9f-120">ホスティングの列挙体</span><span class="sxs-lookup"><span data-stu-id="9ec9f-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
