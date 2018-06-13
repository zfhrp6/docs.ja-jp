---
title: AXL_AUTHENTICODE_TIMESTAMPER_INFO 構造体
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c89845008307e4cfb00d0f9b9a168a43ba5378c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402364"
---
# <a name="axlauthenticodetimestamperinfo-structure"></a><span data-ttu-id="a541d-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="a541d-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>
<span data-ttu-id="a541d-103">Authenticode のタイム スタンパー情報を定義します。</span><span class="sxs-lookup"><span data-stu-id="a541d-103">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a541d-104">構文</span><span class="sxs-lookup"><span data-stu-id="a541d-104">Syntax</span></span>  
  
```  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="a541d-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="a541d-105">Members</span></span>  
  
|<span data-ttu-id="a541d-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="a541d-106">Member</span></span>|<span data-ttu-id="a541d-107">説明</span><span class="sxs-lookup"><span data-stu-id="a541d-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="a541d-108">この構造のサイズ。</span><span class="sxs-lookup"><span data-stu-id="a541d-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="a541d-109">エラー コード。</span><span class="sxs-lookup"><span data-stu-id="a541d-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="a541d-110">ハッシュアルゴリズム。</span><span class="sxs-lookup"><span data-stu-id="a541d-110">The hash algorithm.</span></span>|  
|`ftTimestamp`|<span data-ttu-id="a541d-111">タイム スタンプの時刻。</span><span class="sxs-lookup"><span data-stu-id="a541d-111">The time of the time stamp.</span></span>|  
|`pChainContext`|<span data-ttu-id="a541d-112">タイム スタンパーのチェーン コンテキスト。</span><span class="sxs-lookup"><span data-stu-id="a541d-112">The time stamper’s chain context.</span></span>  <span data-ttu-id="a541d-113">参照してください、 [CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx)構造体。</span><span class="sxs-lookup"><span data-stu-id="a541d-113">See the [CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a541d-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="a541d-114">See Also</span></span>  
 [<span data-ttu-id="a541d-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="a541d-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
