---
title: "ICeeGen::GetSectionBlock メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetSectionBlock
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetSectionBlock
helpviewer_keywords:
- GetSectionBlock method [.NET Framework metadata]
- ICeeGen::GetSectionBlock method [.NET Framework metadata]
ms.assetid: 05c78aaf-5bbd-497e-9ae2-55f4fae0c5fb
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4732eef9a47f9ea1e919bd9d855afbec18974454
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="iceegengetsectionblock-method"></a><span data-ttu-id="d5c85-102">ICeeGen::GetSectionBlock メソッド</span><span class="sxs-lookup"><span data-stu-id="d5c85-102">ICeeGen::GetSectionBlock Method</span></span>
<span data-ttu-id="d5c85-103">コード ベースのセクションのブロックを取得します。</span><span class="sxs-lookup"><span data-stu-id="d5c85-103">Gets a section block of the code base.</span></span>  
  
 <span data-ttu-id="d5c85-104">このメソッドは、古いは使用できません。</span><span class="sxs-lookup"><span data-stu-id="d5c85-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5c85-105">構文</span><span class="sxs-lookup"><span data-stu-id="d5c85-105">Syntax</span></span>  
  
```  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,     
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="d5c85-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d5c85-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="d5c85-107">[in]コード ベースのブロックを取得する対象のセクションです。</span><span class="sxs-lookup"><span data-stu-id="d5c85-107">[in] The section from which to retrieve a block of the code base.</span></span>  
  
 `len`  
 <span data-ttu-id="d5c85-108">[in]取得するブロックの長さ。</span><span class="sxs-lookup"><span data-stu-id="d5c85-108">[in] The length of the block to be retrieved.</span></span>  
  
 `align`  
 <span data-ttu-id="d5c85-109">[in]ブロックの最初のバイトを配置に使用されたセクションの先頭からの相対バイト。</span><span class="sxs-lookup"><span data-stu-id="d5c85-109">[in] The byte, relative to the beginning of the section, with which to align the first byte of the block.</span></span> <span data-ttu-id="d5c85-110">これは、セクション内のブロックの位置です。</span><span class="sxs-lookup"><span data-stu-id="d5c85-110">This is the position of the block within the section.</span></span>  
  
 `ppBytes`  
 <span data-ttu-id="d5c85-111">[out]取得したブロックのアドレスを受け取る場所へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d5c85-111">[out] A pointer to a location that receives the address of the retrieved block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5c85-112">コメント</span><span class="sxs-lookup"><span data-stu-id="d5c85-112">Remarks</span></span>  
 <span data-ttu-id="d5c85-113">呼び出す`GetSectionBlock`他の方法で処理されない特別なセクションの要件がある場合にのみです。</span><span class="sxs-lookup"><span data-stu-id="d5c85-113">Call `GetSectionBlock` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5c85-114">要件</span><span class="sxs-lookup"><span data-stu-id="d5c85-114">Requirements</span></span>  
 <span data-ttu-id="d5c85-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d5c85-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5c85-116">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d5c85-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d5c85-117">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="d5c85-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d5c85-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5c85-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5c85-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5c85-119">See Also</span></span>  
 [<span data-ttu-id="d5c85-120">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d5c85-120">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
