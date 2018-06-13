---
title: ECustomDumpFlavor 列挙型
ms.date: 03/30/2017
api_name:
- ECustomDumpFlavor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ECustomDumpFlavor
helpviewer_keywords:
- ECustomDumpFlavor enumeration [.NET Framework hosting]
ms.assetid: b39b3320-fac7-41f1-9a03-ab6fb0cd89c7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6d0ba3f722f63650a3db6a8f633189993db0716
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431409"
---
# <a name="ecustomdumpflavor-enumeration"></a><span data-ttu-id="fee63-102">ECustomDumpFlavor 列挙型</span><span class="sxs-lookup"><span data-stu-id="fee63-102">ECustomDumpFlavor Enumeration</span></span>
<span data-ttu-id="fee63-103">エラーを報告するときに、ヒープのカスタムのサブセットに含めるには、どの項目がダンプを示す値を含みます。</span><span class="sxs-lookup"><span data-stu-id="fee63-103">Contains values that indicate which items to include in a custom subset of a heap dump when reporting errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fee63-104">構文</span><span class="sxs-lookup"><span data-stu-id="fee63-104">Syntax</span></span>  
  
```  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a><span data-ttu-id="fee63-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="fee63-105">Members</span></span>  
  
|<span data-ttu-id="fee63-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="fee63-106">Member</span></span>|<span data-ttu-id="fee63-107">説明</span><span class="sxs-lookup"><span data-stu-id="fee63-107">Description</span></span>|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|<span data-ttu-id="fee63-108">カスタム ヒープ ダンプする必要があります、ミニダンプとして起動し、いずれかで指定された追加のデータを含めることを示す[CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)インスタンスが同じメソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="fee63-108">Specifies that the custom heap dump should start as a minidump and include extra data specified by any [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances passed to the same method.</span></span>|  
|`DUMP_FLAVOR_NonHeapCLRState`|<span data-ttu-id="fee63-109">カスタム ヒープ ダンプが動的に割り当てられていないすべての実行時の状態データを収集する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="fee63-109">Specifies that the custom heap dump should gather all run-time state data that was not dynamically allocated.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fee63-110">コメント</span><span class="sxs-lookup"><span data-stu-id="fee63-110">Remarks</span></span>  
 <span data-ttu-id="fee63-111">型のパラメーター`ECustomDumpFlavor`に渡される、 [iclrerrorreportingmanager::begincustomdump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="fee63-111">A parameter of type `ECustomDumpFlavor` is passed to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fee63-112">要件</span><span class="sxs-lookup"><span data-stu-id="fee63-112">Requirements</span></span>  
 <span data-ttu-id="fee63-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fee63-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fee63-114">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fee63-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fee63-115">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fee63-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fee63-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fee63-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fee63-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="fee63-117">See Also</span></span>  
 [<span data-ttu-id="fee63-118">ECustomDumpItemKind 列挙型</span><span class="sxs-lookup"><span data-stu-id="fee63-118">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)  
 [<span data-ttu-id="fee63-119">ICLRErrorReportingManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fee63-119">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [<span data-ttu-id="fee63-120">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="fee63-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
