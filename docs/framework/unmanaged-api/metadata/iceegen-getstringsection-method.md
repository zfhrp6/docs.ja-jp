---
title: ICeeGen::GetStringSection メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.GetStringSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetStringSection
helpviewer_keywords:
- ICeeGen::GetStringSection method [.NET Framework metadata]
- GetStringSection method [.NET Framework metadata]
ms.assetid: a2267d39-69d1-4de1-bf37-f752cafacc71
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a8617c9e818ec514c912a85373c916559d89df3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443038"
---
# <a name="iceegengetstringsection-method"></a><span data-ttu-id="db0f1-102">ICeeGen::GetStringSection メソッド</span><span class="sxs-lookup"><span data-stu-id="db0f1-102">ICeeGen::GetStringSection Method</span></span>
<span data-ttu-id="db0f1-103">指定されたハンドルによって参照されるコードのセクションの文字列表現を取得します。</span><span class="sxs-lookup"><span data-stu-id="db0f1-103">Gets a string representation of the code section referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="db0f1-104">このメソッドは、古いは使用できません。</span><span class="sxs-lookup"><span data-stu-id="db0f1-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db0f1-105">構文</span><span class="sxs-lookup"><span data-stu-id="db0f1-105">Syntax</span></span>  
  
```  
HRESULT GetStringSection (  
    [in, out] HCEESECTION     *section  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db0f1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="db0f1-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="db0f1-107">[入力、出力].コード セクションへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="db0f1-107">[in, out] The handle to the code section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db0f1-108">要件</span><span class="sxs-lookup"><span data-stu-id="db0f1-108">Requirements</span></span>  
 <span data-ttu-id="db0f1-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="db0f1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db0f1-110">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="db0f1-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="db0f1-111">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="db0f1-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="db0f1-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db0f1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db0f1-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="db0f1-113">See Also</span></span>  
 [<span data-ttu-id="db0f1-114">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="db0f1-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
