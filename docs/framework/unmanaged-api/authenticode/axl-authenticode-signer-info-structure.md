---
title: AXL_AUTHENTICODE_SIGNER_INFO 構造体
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd07707b5a80ec0980fc50b27caddf0a24398fd1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400446"
---
# <a name="axlauthenticodesignerinfo-structure"></a><span data-ttu-id="81f7d-102">AXL_AUTHENTICODE_SIGNER_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="81f7d-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="81f7d-103">Authenticode の署名者情報を定義します。</span><span class="sxs-lookup"><span data-stu-id="81f7d-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81f7d-104">構文</span><span class="sxs-lookup"><span data-stu-id="81f7d-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="81f7d-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="81f7d-105">Members</span></span>  
  
|<span data-ttu-id="81f7d-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="81f7d-106">Member</span></span>|<span data-ttu-id="81f7d-107">説明</span><span class="sxs-lookup"><span data-stu-id="81f7d-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="81f7d-108">この構造のサイズ。</span><span class="sxs-lookup"><span data-stu-id="81f7d-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="81f7d-109">エラー コード。</span><span class="sxs-lookup"><span data-stu-id="81f7d-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="81f7d-110">ハッシュアルゴリズム。</span><span class="sxs-lookup"><span data-stu-id="81f7d-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="81f7d-111">ハッシュ。</span><span class="sxs-lookup"><span data-stu-id="81f7d-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="81f7d-112">説明。</span><span class="sxs-lookup"><span data-stu-id="81f7d-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="81f7d-113">説明の URL。</span><span class="sxs-lookup"><span data-stu-id="81f7d-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="81f7d-114">署名者のチェーン コンテキスト。</span><span class="sxs-lookup"><span data-stu-id="81f7d-114">The chain context of the signer.</span></span> <span data-ttu-id="81f7d-115">参照してください、 [CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx)構造体。</span><span class="sxs-lookup"><span data-stu-id="81f7d-115">See the [CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81f7d-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="81f7d-116">See Also</span></span>  
 [<span data-ttu-id="81f7d-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="81f7d-117">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
