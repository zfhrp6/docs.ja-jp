---
title: COUNINITIEE 列挙型
ms.date: 03/30/2017
api_name:
- COUNINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COUNINITIEE
helpviewer_keywords:
- COUNINITIEE enumeration [.NET Framework metadata]
ms.assetid: c42baa79-f469-4330-95a2-baf7f021c2fc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dcd7dc7c51caa94308760c0086384c8eea184ee9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443598"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="aa57c-102">COUNINITIEE 列挙型</span><span class="sxs-lookup"><span data-stu-id="aa57c-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="aa57c-103">によって使用される定数を指定[CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md)共通言語ランタイムを初期化するときにします。</span><span class="sxs-lookup"><span data-stu-id="aa57c-103">Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa57c-104">構文</span><span class="sxs-lookup"><span data-stu-id="aa57c-104">Syntax</span></span>  
  
```  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,   
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="aa57c-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="aa57c-105">Members</span></span>  
  
|<span data-ttu-id="aa57c-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="aa57c-106">Member</span></span>|<span data-ttu-id="aa57c-107">説明</span><span class="sxs-lookup"><span data-stu-id="aa57c-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="aa57c-108">既定の初期化解除モードを示します。</span><span class="sxs-lookup"><span data-stu-id="aa57c-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="aa57c-109">アセンブリをアンロードするための初期化解除モードを示します。</span><span class="sxs-lookup"><span data-stu-id="aa57c-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aa57c-110">要件</span><span class="sxs-lookup"><span data-stu-id="aa57c-110">Requirements</span></span>  
 <span data-ttu-id="aa57c-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="aa57c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa57c-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="aa57c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aa57c-113">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="aa57c-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aa57c-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa57c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa57c-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="aa57c-115">See Also</span></span>  
 [<span data-ttu-id="aa57c-116">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="aa57c-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
