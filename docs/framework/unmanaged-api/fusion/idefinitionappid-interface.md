---
title: "IDefinitionAppId インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDefinitionAppId
api_location: fusion.dll
api_type: COM
f1_keywords: IDefinitionAppId
helpviewer_keywords: IDefinitionAppId interface [.NET Framework fusion]
ms.assetid: e72f2550-bdec-4a20-a2f4-2e14847266c1
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 247edbe300bbb93ddbdd4260109999fd33b08006
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idefinitionappid-interface"></a><span data-ttu-id="be0c1-102">IDefinitionAppId インターフェイス</span><span class="sxs-lookup"><span data-stu-id="be0c1-102">IDefinitionAppId Interface</span></span>
<span data-ttu-id="be0c1-103">現在のスコープで、アプリケーションを定義するコードの一意の識別子を表します。</span><span class="sxs-lookup"><span data-stu-id="be0c1-103">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="be0c1-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="be0c1-104">Methods</span></span>  
  
|<span data-ttu-id="be0c1-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="be0c1-105">Method</span></span>|<span data-ttu-id="be0c1-106">説明</span><span class="sxs-lookup"><span data-stu-id="be0c1-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|<span data-ttu-id="be0c1-107">このコードを表す書式設定された文字列を取得`IDefinitionAppId`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="be0c1-107">Gets a formatted string that represents the code in this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_Codebase`|<span data-ttu-id="be0c1-108">このコード設定`IDefinitionAppId`を指定したオブジェクトの書式設定された文字列値です。</span><span class="sxs-lookup"><span data-stu-id="be0c1-108">Sets the code of this `IDefinitionAppId` object to the specified formatted string value.</span></span>|  
|`IDefinitionAppId::EnumAppPath`|<span data-ttu-id="be0c1-109">インターフェイス ポインターを取得、 [IEnumDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md)を現在のアプリケーション パス内のアセンブリを含むオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="be0c1-109">Gets an interface pointer to an [IEnumDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md) object that contains the assemblies in the current application path.</span></span>|  
|`IDefinitionAppId::SetAppPath`|<span data-ttu-id="be0c1-110">アセンブリの指定したによって参照される値を現在のスコープでアプリケーションのパスを設定[IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="be0c1-110">Sets the application path for the assembly in the current scope to the value referenced by the specified [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) object.</span></span>|  
|`IDefinitionAppId::get_SubscriptionId`|<span data-ttu-id="be0c1-111">このサブスクリプションのトークンの id の文字列形式へのポインターを取得`IDefinitionAppId`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="be0c1-111">Gets a pointer to a string representation of the token identifier for a subscription to this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_SubscriptionId`|<span data-ttu-id="be0c1-112">このサブスクリプションのトークンの識別子を設定`IDefinitionAppId`オブジェクトを指定した文字列値にします。</span><span class="sxs-lookup"><span data-stu-id="be0c1-112">Sets the token identifier for a subscription to this `IDefinitionAppId` object to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="be0c1-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="be0c1-113">Requirements</span></span>  
 <span data-ttu-id="be0c1-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="be0c1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be0c1-115">**ヘッダー:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="be0c1-115">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="be0c1-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be0c1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be0c1-117">参照</span><span class="sxs-lookup"><span data-stu-id="be0c1-117">See Also</span></span>  
 [<span data-ttu-id="be0c1-118">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="be0c1-118">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
