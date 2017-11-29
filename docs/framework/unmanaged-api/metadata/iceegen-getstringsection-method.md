---
title: "ICeeGen::GetStringSection メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetStringSection
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetStringSection
helpviewer_keywords:
- ICeeGen::GetStringSection method [.NET Framework metadata]
- GetStringSection method [.NET Framework metadata]
ms.assetid: a2267d39-69d1-4de1-bf37-f752cafacc71
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ce511b4610a6ff681eb70bfeb6a7a7afe162818e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="iceegengetstringsection-method"></a><span data-ttu-id="fce26-102">ICeeGen::GetStringSection メソッド</span><span class="sxs-lookup"><span data-stu-id="fce26-102">ICeeGen::GetStringSection Method</span></span>
<span data-ttu-id="fce26-103">指定されたハンドルによって参照されるコードのセクションの文字列表現を取得します。</span><span class="sxs-lookup"><span data-stu-id="fce26-103">Gets a string representation of the code section referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="fce26-104">このメソッドは、古いは使用できません。</span><span class="sxs-lookup"><span data-stu-id="fce26-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fce26-105">構文</span><span class="sxs-lookup"><span data-stu-id="fce26-105">Syntax</span></span>  
  
```  
HRESULT GetStringSection (  
    [in, out] HCEESECTION     *section  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fce26-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fce26-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="fce26-107">[入力、出力].コード セクションへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="fce26-107">[in, out] The handle to the code section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fce26-108">要件</span><span class="sxs-lookup"><span data-stu-id="fce26-108">Requirements</span></span>  
 <span data-ttu-id="fce26-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fce26-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fce26-110">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fce26-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fce26-111">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="fce26-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fce26-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fce26-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fce26-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="fce26-113">See Also</span></span>  
 [<span data-ttu-id="fce26-114">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fce26-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
