---
title: "ICLRHostProtectionManager インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostProtectionManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostProtectionManager
helpviewer_keywords: ICLRHostProtectionManager interface [.NET Framework hosting]
ms.assetid: ce2770ae-23d0-45d9-8bcf-46504ac5020e
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c88279eb26b819adaaaf86dcf59105c6ac728017
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="36f97-102">ICLRHostProtectionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="36f97-102">ICLRHostProtectionManager Interface</span></span>
<span data-ttu-id="36f97-103">特定のマネージ クラス、メソッド、プロパティ、およびフィールド部分的に信頼されたコードでの実行をブロックするホストを有効にします。</span><span class="sxs-lookup"><span data-stu-id="36f97-103">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="36f97-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="36f97-104">Methods</span></span>  
  
|<span data-ttu-id="36f97-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="36f97-105">Method</span></span>|<span data-ttu-id="36f97-106">説明</span><span class="sxs-lookup"><span data-stu-id="36f97-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="36f97-107">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="36f97-107">SetEagerSerializeGrantSets</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="36f97-108">致命的な共通言語ランタイム (CLR) のエラーが発生する特定のまれな競合状態は決して発生しないように保証を提供します。</span><span class="sxs-lookup"><span data-stu-id="36f97-108">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="36f97-109">SetProtectedCategories メソッド</span><span class="sxs-lookup"><span data-stu-id="36f97-109">SetProtectedCategories Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="36f97-110">マネージ型とは、部分信頼コードでの実行をブロックするメンバーのカテゴリを指定します。</span><span class="sxs-lookup"><span data-stu-id="36f97-110">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="36f97-111">要件</span><span class="sxs-lookup"><span data-stu-id="36f97-111">Requirements</span></span>  
 <span data-ttu-id="36f97-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="36f97-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36f97-113">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="36f97-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="36f97-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="36f97-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="36f97-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36f97-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36f97-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="36f97-116">See Also</span></span>  
 [<span data-ttu-id="36f97-117">EApiCategories 列挙型</span><span class="sxs-lookup"><span data-stu-id="36f97-117">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)  
 [<span data-ttu-id="36f97-118">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="36f97-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
