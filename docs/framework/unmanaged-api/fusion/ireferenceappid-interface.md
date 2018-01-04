---
title: "IReferenceAppId インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IReferenceAppId
api_location: fusion.dll
api_type: COM
f1_keywords: IReferenceAppId
helpviewer_keywords: IReferenceAppId interface [.NET Framework fusion]
ms.assetid: 8eb9e565-f358-43ce-900e-a8f8a5aa6cfb
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 22ac2d75632b3c670d7c185cbbf5081732dcaffc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="08c74-102">IReferenceAppId インターフェイス</span><span class="sxs-lookup"><span data-stu-id="08c74-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="08c74-103">現在のスコープ内のアプリケーションの一意識別子への参照を表します。</span><span class="sxs-lookup"><span data-stu-id="08c74-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="08c74-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="08c74-104">Methods</span></span>  
  
|<span data-ttu-id="08c74-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="08c74-105">Method</span></span>|<span data-ttu-id="08c74-106">説明</span><span class="sxs-lookup"><span data-stu-id="08c74-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="08c74-107">これによって参照されているアプリケーションのコードの識別子の文字列表記にポインターを取得`IReferenceAppId`です。</span><span class="sxs-lookup"><span data-stu-id="08c74-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="08c74-108">これによって参照されているアプリケーションのコードの識別子を設定`IReferenceAppId`です。</span><span class="sxs-lookup"><span data-stu-id="08c74-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="08c74-109">インターフェイス ポインターを取得、`IEnumReferenceIdentity`インスタンスを含む、 `IReferenceIdentity` this のメンバーを表すインスタンス`IReferenceAppId`です。</span><span class="sxs-lookup"><span data-stu-id="08c74-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="08c74-110">このサブスクリプションのトークンの id の文字列形式へのポインターを取得`IReferenceAppId`です。</span><span class="sxs-lookup"><span data-stu-id="08c74-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="08c74-111">このサブスクリプションのトークンの識別子を設定`IReferenceAppId`に指定した文字列値です。</span><span class="sxs-lookup"><span data-stu-id="08c74-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="08c74-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="08c74-112">Requirements</span></span>  
 <span data-ttu-id="08c74-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="08c74-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08c74-114">**ヘッダー:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="08c74-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="08c74-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08c74-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08c74-116">参照</span><span class="sxs-lookup"><span data-stu-id="08c74-116">See Also</span></span>  
 [<span data-ttu-id="08c74-117">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="08c74-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="08c74-118">IEnumReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="08c74-118">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 [<span data-ttu-id="08c74-119">IReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="08c74-119">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
