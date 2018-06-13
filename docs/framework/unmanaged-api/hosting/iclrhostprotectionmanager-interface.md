---
title: ICLRHostProtectionManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager
helpviewer_keywords:
- ICLRHostProtectionManager interface [.NET Framework hosting]
ms.assetid: ce2770ae-23d0-45d9-8bcf-46504ac5020e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c630fcd4667c8b19c4e21335549674d32508e439
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432837"
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="892c4-102">ICLRHostProtectionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="892c4-102">ICLRHostProtectionManager Interface</span></span>
<span data-ttu-id="892c4-103">特定のマネージ クラス、メソッド、プロパティ、およびフィールド部分的に信頼されたコードでの実行をブロックするホストを有効にします。</span><span class="sxs-lookup"><span data-stu-id="892c4-103">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="892c4-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="892c4-104">Methods</span></span>  
  
|<span data-ttu-id="892c4-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="892c4-105">Method</span></span>|<span data-ttu-id="892c4-106">説明</span><span class="sxs-lookup"><span data-stu-id="892c4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="892c4-107">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="892c4-107">SetEagerSerializeGrantSets</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="892c4-108">致命的な共通言語ランタイム (CLR) のエラーが発生する特定のまれな競合状態は決して発生しないように保証を提供します。</span><span class="sxs-lookup"><span data-stu-id="892c4-108">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="892c4-109">SetProtectedCategories メソッド</span><span class="sxs-lookup"><span data-stu-id="892c4-109">SetProtectedCategories Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="892c4-110">マネージ型とは、部分信頼コードでの実行をブロックするメンバーのカテゴリを指定します。</span><span class="sxs-lookup"><span data-stu-id="892c4-110">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="892c4-111">要件</span><span class="sxs-lookup"><span data-stu-id="892c4-111">Requirements</span></span>  
 <span data-ttu-id="892c4-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="892c4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="892c4-113">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="892c4-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="892c4-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="892c4-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="892c4-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="892c4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="892c4-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="892c4-116">See Also</span></span>  
 [<span data-ttu-id="892c4-117">EApiCategories 列挙型</span><span class="sxs-lookup"><span data-stu-id="892c4-117">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)  
 [<span data-ttu-id="892c4-118">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="892c4-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
