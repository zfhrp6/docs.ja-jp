---
title: "AXL_AUTHENTICODE_SIGNER_INFO 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c53ca8073adda5cba497e9f45404024435cc161f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="axlauthenticodesignerinfo-structure"></a><span data-ttu-id="87ab4-102">AXL_AUTHENTICODE_SIGNER_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="87ab4-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="87ab4-103">Authenticode の署名者情報を定義します。</span><span class="sxs-lookup"><span data-stu-id="87ab4-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87ab4-104">構文</span><span class="sxs-lookup"><span data-stu-id="87ab4-104">Syntax</span></span>  
  
```  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    LPCWSTR pwszHash  
    LPCWSTR pwszDescription;  
    LPCWSTR pwszDescriptionUrl;  
    PCCERT_CHAIN_CONTEXT pChainContext  
} AXL_AUTHENTICODE_SIGNER_INFO, * PAXL_AUTHENTICODE_SIGNER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="87ab4-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="87ab4-105">Members</span></span>  
  
|<span data-ttu-id="87ab4-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="87ab4-106">Member</span></span>|<span data-ttu-id="87ab4-107">説明</span><span class="sxs-lookup"><span data-stu-id="87ab4-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="87ab4-108">この構造のサイズ。</span><span class="sxs-lookup"><span data-stu-id="87ab4-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="87ab4-109">エラー コード。</span><span class="sxs-lookup"><span data-stu-id="87ab4-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="87ab4-110">ハッシュアルゴリズム。</span><span class="sxs-lookup"><span data-stu-id="87ab4-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="87ab4-111">ハッシュ。</span><span class="sxs-lookup"><span data-stu-id="87ab4-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="87ab4-112">説明。</span><span class="sxs-lookup"><span data-stu-id="87ab4-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="87ab4-113">説明の URL。</span><span class="sxs-lookup"><span data-stu-id="87ab4-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="87ab4-114">署名者のチェーン コンテキスト。</span><span class="sxs-lookup"><span data-stu-id="87ab4-114">The chain context of the signer.</span></span> <span data-ttu-id="87ab4-115">参照してください、 [CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx)構造体。</span><span class="sxs-lookup"><span data-stu-id="87ab4-115">See the [CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="87ab4-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="87ab4-116">See Also</span></span>  
 [<span data-ttu-id="87ab4-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="87ab4-117">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
