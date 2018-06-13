---
title: ICeeGen::TruncateSection メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.TruncateSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::TruncateSection
helpviewer_keywords:
- TruncateSection method [.NET Framework metadata]
- ICeeGen::TruncateSection method [.NET Framework metadata]
ms.assetid: 0451d752-1e5c-4c9a-8bad-6cd35b7ba3df
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a7b21179faec0b6f37b8084c9ee8a0bfd327193e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443565"
---
# <a name="iceegentruncatesection-method"></a><span data-ttu-id="96ed5-102">ICeeGen::TruncateSection メソッド</span><span class="sxs-lookup"><span data-stu-id="96ed5-102">ICeeGen::TruncateSection Method</span></span>
<span data-ttu-id="96ed5-103">指定された長さで指定したコードのセクションを切り捨てます。</span><span class="sxs-lookup"><span data-stu-id="96ed5-103">Truncates the specified code section by the specified length.</span></span>  
  
 <span data-ttu-id="96ed5-104">このメソッドは、古いは使用できません。</span><span class="sxs-lookup"><span data-stu-id="96ed5-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96ed5-105">構文</span><span class="sxs-lookup"><span data-stu-id="96ed5-105">Syntax</span></span>  
  
```  
HRESULT TruncateSection (  
    [in]  HCEESECTION     section,  
    [in]  ULONG           len  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="96ed5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="96ed5-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="96ed5-107">[in]切り捨てを行うためのセクションです。</span><span class="sxs-lookup"><span data-stu-id="96ed5-107">[in] The section to truncate.</span></span>  
  
 `len`  
 <span data-ttu-id="96ed5-108">[in]セクションを切り捨てるに使用する、バイト単位の長さ。</span><span class="sxs-lookup"><span data-stu-id="96ed5-108">[in] The length, in bytes, by which to truncate the section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96ed5-109">コメント</span><span class="sxs-lookup"><span data-stu-id="96ed5-109">Remarks</span></span>  
 <span data-ttu-id="96ed5-110">呼び出す`TruncateSection`他の方法で処理されない特別なセクションの要件がある場合にのみです。</span><span class="sxs-lookup"><span data-stu-id="96ed5-110">Call `TruncateSection` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96ed5-111">要件</span><span class="sxs-lookup"><span data-stu-id="96ed5-111">Requirements</span></span>  
 <span data-ttu-id="96ed5-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="96ed5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96ed5-113">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="96ed5-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="96ed5-114">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="96ed5-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="96ed5-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96ed5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96ed5-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="96ed5-116">See Also</span></span>  
 [<span data-ttu-id="96ed5-117">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="96ed5-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
