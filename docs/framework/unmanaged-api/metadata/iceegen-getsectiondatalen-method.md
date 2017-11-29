---
title: "ICeeGen::GetSectionDataLen メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetSectionDataLen
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetSectionDataLen
helpviewer_keywords:
- ICeeGen::GetSectionDataLen method [.NET Framework metadata]
- GetSectionDataLen method [.NET Framework metadata]
ms.assetid: e2a06ee4-b8ee-49c7-935a-c1031a29eef2
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7d119fdfe5c0202d08ca78026a6917bb4ef51422
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="8f16e-102">ICeeGen::GetSectionDataLen メソッド</span><span class="sxs-lookup"><span data-stu-id="8f16e-102">ICeeGen::GetSectionDataLen Method</span></span>
<span data-ttu-id="8f16e-103">指定されたセクションの長さを取得します。</span><span class="sxs-lookup"><span data-stu-id="8f16e-103">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="8f16e-104">このメソッドは、古いは使用できません。</span><span class="sxs-lookup"><span data-stu-id="8f16e-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f16e-105">構文</span><span class="sxs-lookup"><span data-stu-id="8f16e-105">Syntax</span></span>  
  
```  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8f16e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8f16e-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="8f16e-107">[in]セクション「データの長さが取得されます。</span><span class="sxs-lookup"><span data-stu-id="8f16e-107">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="8f16e-108">[out]指定されたセクションの返される長さ。</span><span class="sxs-lookup"><span data-stu-id="8f16e-108">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f16e-109">コメント</span><span class="sxs-lookup"><span data-stu-id="8f16e-109">Remarks</span></span>  
 <span data-ttu-id="8f16e-110">呼び出す`GetSectionDataLen`他の方法で処理されない特別なセクションの要件がある場合にのみです。</span><span class="sxs-lookup"><span data-stu-id="8f16e-110">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f16e-111">要件</span><span class="sxs-lookup"><span data-stu-id="8f16e-111">Requirements</span></span>  
 <span data-ttu-id="8f16e-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8f16e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f16e-113">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8f16e-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8f16e-114">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="8f16e-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8f16e-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f16e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f16e-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="8f16e-116">See Also</span></span>  
 [<span data-ttu-id="8f16e-117">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8f16e-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
