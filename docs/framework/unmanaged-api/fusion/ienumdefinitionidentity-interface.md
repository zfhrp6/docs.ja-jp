---
title: "IEnumDefinitionIdentity インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IEnumDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumDefinitionIdentity
helpviewer_keywords:
- IEnumDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: 8263e75d-251b-4abc-8a1a-c62884142232
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 79e2a35a455407715a05e826d31c5d5ab05a02ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdefinitionidentity-interface"></a><span data-ttu-id="607a7-102">IEnumDefinitionIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="607a7-102">IEnumDefinitionIdentity Interface</span></span>
<span data-ttu-id="607a7-103">コレクションの列挙子の役割を果たす`IDefinitionIdentity`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="607a7-103">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="607a7-104">構文</span><span class="sxs-lookup"><span data-stu-id="607a7-104">Syntax</span></span>  
  
```  
IEnumDefinitionIdentity : IUnknown {  
  
    HRESULT Clone (  
        [out] IEnumDefinitionIdentity **ppIEnumDefinitionIdentity  
    );  
  
    HRESULT Next (  
        [in]  ULONG               celt,  
        [out, length_is(celt), size_is(*pceltWritten)]  
              IDefinitionIdentity *rgpIDefinitionIdentity[],  
        [out] ULONG               *pceltWritten  
    );  
  
    HRESULT Reset ();  
  
    HRESULT Skip (  
        [in] ULONG celt  
    );  
  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="607a7-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="607a7-105">Methods</span></span>  
  
|<span data-ttu-id="607a7-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="607a7-106">Method</span></span>|<span data-ttu-id="607a7-107">説明</span><span class="sxs-lookup"><span data-stu-id="607a7-107">Description</span></span>|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|<span data-ttu-id="607a7-108">新しいインターフェイス ポインターを取得`IEnumDefinitionIdentity`これと同じメンバーを格納しているオブジェクト`IEnumDefinitionIdentity`です。</span><span class="sxs-lookup"><span data-stu-id="607a7-108">Gets an interface pointer to a new `IEnumDefinitionIdentity` object that contains the same members as this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Next`|<span data-ttu-id="607a7-109">指定した数を取得`IDefinitionIdentity`オブジェクト、現在の位置で開始します。</span><span class="sxs-lookup"><span data-stu-id="607a7-109">Gets the specified number of `IDefinitionIdentity` objects, starting at the current position.</span></span>|  
|`IEnumDefinitionIdentity::Reset`|<span data-ttu-id="607a7-110">これの先頭に、命令ポインターを移動`IEnumDefinitionIdentity`です。</span><span class="sxs-lookup"><span data-stu-id="607a7-110">Moves the instruction pointer to the beginning of this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Skip`|<span data-ttu-id="607a7-111">指定した数の現在位置の要素では、命令ポインターを前方を移動します。</span><span class="sxs-lookup"><span data-stu-id="607a7-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="607a7-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="607a7-112">Requirements</span></span>  
 <span data-ttu-id="607a7-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="607a7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="607a7-114">**ヘッダー:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="607a7-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="607a7-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="607a7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="607a7-116">参照</span><span class="sxs-lookup"><span data-stu-id="607a7-116">See Also</span></span>  
 [<span data-ttu-id="607a7-117">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="607a7-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="607a7-118">IDefinitionIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="607a7-118">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
