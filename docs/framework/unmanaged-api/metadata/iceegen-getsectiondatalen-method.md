---
title: "ICeeGen::GetSectionDataLen メソッド"
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
- ICeeGen.GetSectionDataLen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionDataLen
helpviewer_keywords:
- ICeeGen::GetSectionDataLen method [.NET Framework metadata]
- GetSectionDataLen method [.NET Framework metadata]
ms.assetid: e2a06ee4-b8ee-49c7-935a-c1031a29eef2
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 217a6c87d5152b68e062d9c2a64ec78478f301cd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="94fe8-102">ICeeGen::GetSectionDataLen メソッド</span><span class="sxs-lookup"><span data-stu-id="94fe8-102">ICeeGen::GetSectionDataLen Method</span></span>
<span data-ttu-id="94fe8-103">指定されたセクションの長さを取得します。</span><span class="sxs-lookup"><span data-stu-id="94fe8-103">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="94fe8-104">このメソッドは、古いは使用できません。</span><span class="sxs-lookup"><span data-stu-id="94fe8-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94fe8-105">構文</span><span class="sxs-lookup"><span data-stu-id="94fe8-105">Syntax</span></span>  
  
```  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="94fe8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="94fe8-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="94fe8-107">[in]セクション「データの長さが取得されます。</span><span class="sxs-lookup"><span data-stu-id="94fe8-107">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="94fe8-108">[out]指定されたセクションの返される長さ。</span><span class="sxs-lookup"><span data-stu-id="94fe8-108">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94fe8-109">コメント</span><span class="sxs-lookup"><span data-stu-id="94fe8-109">Remarks</span></span>  
 <span data-ttu-id="94fe8-110">呼び出す`GetSectionDataLen`他の方法で処理されない特別なセクションの要件がある場合にのみです。</span><span class="sxs-lookup"><span data-stu-id="94fe8-110">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94fe8-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="94fe8-111">Requirements</span></span>  
 <span data-ttu-id="94fe8-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="94fe8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94fe8-113">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="94fe8-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="94fe8-114">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="94fe8-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="94fe8-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94fe8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94fe8-116">参照</span><span class="sxs-lookup"><span data-stu-id="94fe8-116">See Also</span></span>  
 [<span data-ttu-id="94fe8-117">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="94fe8-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
