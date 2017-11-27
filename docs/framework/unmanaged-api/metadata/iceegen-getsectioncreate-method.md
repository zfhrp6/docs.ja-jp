---
title: "ICeeGen::GetSectionCreate メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetSectionCreate
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetSectionCreate
helpviewer_keywords:
- ICeeGen::GetSectionCreate method [.NET Framework metadata]
- GetSectionCreate method [.NET Framework metadata]
ms.assetid: 154b2460-59ce-4874-a9f2-1b3353486ac5
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2ea9cb20b62e1b1fa8e726ba0c49c5e24202530c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="iceegengetsectioncreate-method"></a><span data-ttu-id="8dee3-102">ICeeGen::GetSectionCreate メソッド</span><span class="sxs-lookup"><span data-stu-id="8dee3-102">ICeeGen::GetSectionCreate Method</span></span>
<span data-ttu-id="8dee3-103">生成し、指定した名前とフラグの値を使用してコード セクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="8dee3-103">Generates and gets a code section using the specified name and flag values.</span></span>  
  
 <span data-ttu-id="8dee3-104">このメソッドは、古いは使用できません。</span><span class="sxs-lookup"><span data-stu-id="8dee3-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dee3-105">構文</span><span class="sxs-lookup"><span data-stu-id="8dee3-105">Syntax</span></span>  
  
```  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8dee3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8dee3-106">Parameters</span></span>  
 `name`  
 <span data-ttu-id="8dee3-107">[in]作成するのには、セクションの名前を指定する文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8dee3-107">[in] A pointer to a string that specifies the name of the section to be created.</span></span>  
  
 `flags`  
 <span data-ttu-id="8dee3-108">[in]オプションを指定するフラグ。</span><span class="sxs-lookup"><span data-stu-id="8dee3-108">[in] Flags that specify options.</span></span>  
  
 `section`  
 <span data-ttu-id="8dee3-109">[out]新しく作成されたコード セクションへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8dee3-109">[out] A pointer to the newly created code section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8dee3-110">コメント</span><span class="sxs-lookup"><span data-stu-id="8dee3-110">Remarks</span></span>  
 <span data-ttu-id="8dee3-111">呼び出す`GetSectionCreate`他の方法で処理されない特別なセクションの要件がある場合にのみです。</span><span class="sxs-lookup"><span data-stu-id="8dee3-111">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8dee3-112">要件</span><span class="sxs-lookup"><span data-stu-id="8dee3-112">Requirements</span></span>  
 <span data-ttu-id="8dee3-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8dee3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8dee3-114">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8dee3-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8dee3-115">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="8dee3-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8dee3-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8dee3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dee3-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="8dee3-117">See Also</span></span>  
 [<span data-ttu-id="8dee3-118">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8dee3-118">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
