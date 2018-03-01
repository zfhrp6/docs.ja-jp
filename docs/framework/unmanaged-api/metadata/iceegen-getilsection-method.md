---
title: "ICeeGen::GetIlSection メソッド"
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
- ICeeGen.GetIlSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetIlSection
helpviewer_keywords:
- GetIlSection method [.NET Framework metadata]
- ICeeGen::GetIlSection method [.NET Framework metadata]
ms.assetid: 6f2db2ca-203f-4ac3-9530-208642ca385e
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4805e9421a80954c01ba1ffb6e04332c07e5d84e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iceegengetilsection-method"></a><span data-ttu-id="8da71-102">ICeeGen::GetIlSection メソッド</span><span class="sxs-lookup"><span data-stu-id="8da71-102">ICeeGen::GetIlSection Method</span></span>
<span data-ttu-id="8da71-103">指定されたハンドルによって参照される基本の中間言語コードのセクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="8da71-103">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="8da71-104">このメソッドは、古いは使用できません。</span><span class="sxs-lookup"><span data-stu-id="8da71-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8da71-105">構文</span><span class="sxs-lookup"><span data-stu-id="8da71-105">Syntax</span></span>  
  
```  
HRESULT GetIlSection (  
    [in] HCEESECTION  *section  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8da71-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8da71-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="8da71-107">[in]取得するセクションへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="8da71-107">[in] The handle to the section to get.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8da71-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="8da71-108">Requirements</span></span>  
 <span data-ttu-id="8da71-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8da71-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8da71-110">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8da71-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8da71-111">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="8da71-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8da71-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8da71-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8da71-113">参照</span><span class="sxs-lookup"><span data-stu-id="8da71-113">See Also</span></span>  
 [<span data-ttu-id="8da71-114">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8da71-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
