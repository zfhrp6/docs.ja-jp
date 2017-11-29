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
ms.openlocfilehash: cac4ef63292f1bd342bb94799872b002fdcdf945
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ireferenceappid-interface"></a><span data-ttu-id="2cc7a-102">IReferenceAppId インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2cc7a-102">IReferenceAppId Interface</span></span>
<span data-ttu-id="2cc7a-103">現在のスコープ内のアプリケーションの一意識別子への参照を表します。</span><span class="sxs-lookup"><span data-stu-id="2cc7a-103">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2cc7a-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="2cc7a-104">Methods</span></span>  
  
|<span data-ttu-id="2cc7a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="2cc7a-105">Method</span></span>|<span data-ttu-id="2cc7a-106">説明</span><span class="sxs-lookup"><span data-stu-id="2cc7a-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|<span data-ttu-id="2cc7a-107">これによって参照されているアプリケーションのコードの識別子の文字列表記にポインターを取得`IReferenceAppId`です。</span><span class="sxs-lookup"><span data-stu-id="2cc7a-107">Gets a pointer to a string representation of the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_CodeBase`|<span data-ttu-id="2cc7a-108">これによって参照されているアプリケーションのコードの識別子を設定`IReferenceAppId`です。</span><span class="sxs-lookup"><span data-stu-id="2cc7a-108">Sets the code identifier for the application referenced by this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::EnumAppPath`|<span data-ttu-id="2cc7a-109">インターフェイス ポインターを取得、`IEnumReferenceIdentity`インスタンスを含む、 `IReferenceIdentity` this のメンバーを表すインスタンス`IReferenceAppId`です。</span><span class="sxs-lookup"><span data-stu-id="2cc7a-109">Gets an interface pointer to an `IEnumReferenceIdentity` instance containing the `IReferenceIdentity` instances that represent members of this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::get_SubscriptionId`|<span data-ttu-id="2cc7a-110">このサブスクリプションのトークンの id の文字列形式へのポインターを取得`IReferenceAppId`です。</span><span class="sxs-lookup"><span data-stu-id="2cc7a-110">Gets a pointer to a string representation of the token identifier for a subscription to this `IReferenceAppId`.</span></span>|  
|`IReferenceAppId::put_SubscriptionId`|<span data-ttu-id="2cc7a-111">このサブスクリプションのトークンの識別子を設定`IReferenceAppId`に指定した文字列値です。</span><span class="sxs-lookup"><span data-stu-id="2cc7a-111">Sets the token identifier for a subscription to this `IReferenceAppId` to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2cc7a-112">要件</span><span class="sxs-lookup"><span data-stu-id="2cc7a-112">Requirements</span></span>  
 <span data-ttu-id="2cc7a-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2cc7a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cc7a-114">**ヘッダー:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="2cc7a-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="2cc7a-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cc7a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cc7a-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="2cc7a-116">See Also</span></span>  
 [<span data-ttu-id="2cc7a-117">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2cc7a-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="2cc7a-118">IEnumReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2cc7a-118">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 [<span data-ttu-id="2cc7a-119">IReferenceIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2cc7a-119">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
