---
title: "IDefinitionIdentity インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDefinitionIdentity
api_location: fusion.dll
api_type: COM
f1_keywords: IDefinitionIdentity
helpviewer_keywords: IDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: ce5ba888-5fbe-4efd-91cf-f0ff94d8428b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a63436f107a2604fd5620854339447a4af254e52
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="idefinitionidentity-interface"></a><span data-ttu-id="60c11-102">IDefinitionIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="60c11-102">IDefinitionIdentity Interface</span></span>
<span data-ttu-id="60c11-103">現在のスコープで、アプリケーションを定義するコードの一意のシグネチャを表します。</span><span class="sxs-lookup"><span data-stu-id="60c11-103">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="60c11-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="60c11-104">Methods</span></span>  
  
|<span data-ttu-id="60c11-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="60c11-105">Method</span></span>|<span data-ttu-id="60c11-106">説明</span><span class="sxs-lookup"><span data-stu-id="60c11-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|<span data-ttu-id="60c11-107">新しいインターフェイス ポインターを取得`IDefinitionIdentity`これと同じであるオブジェクト`IDefinitionIdentity`、指定した属性の変更を除きです。</span><span class="sxs-lookup"><span data-stu-id="60c11-107">Gets an interface pointer to a new `IDefinitionIdentity` object that is identical to this `IDefinitionIdentity`, except for the specified attribute changes.</span></span>|  
|`IDefinitionIdentity::EnumAttributes`|<span data-ttu-id="60c11-108">インターフェイス ポインターを取得、 [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)オブジェクトに関連付けられた属性を含む`IDefinitionIdentity`です。</span><span class="sxs-lookup"><span data-stu-id="60c11-108">Gets an interface pointer to an [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) object that contains the attributes associated with this `IDefinitionIdentity`.</span></span>|  
|`IDefinitionIdentity::GetAttribute`|<span data-ttu-id="60c11-109">指定した名前空間内の指定した名前の属性の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="60c11-109">Gets the value of the attribute with the specified name in the specified namespace.</span></span>|  
|`IDefinitionIdentity::SetAttribute`|<span data-ttu-id="60c11-110">指定した値を指定した名前空間で指定した名前を持つ属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="60c11-110">Sets the attribute that has the specified name in the specified namespace to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="60c11-111">要件</span><span class="sxs-lookup"><span data-stu-id="60c11-111">Requirements</span></span>  
 <span data-ttu-id="60c11-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="60c11-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60c11-113">**ヘッダー:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="60c11-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="60c11-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60c11-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60c11-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="60c11-115">See Also</span></span>  
 [<span data-ttu-id="60c11-116">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="60c11-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
