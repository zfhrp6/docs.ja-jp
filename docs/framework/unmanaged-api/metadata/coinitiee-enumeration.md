---
title: "COINITIEE 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COINITIEE
api_location: mscoree.dll
api_type: COM
f1_keywords: COINITIEE
helpviewer_keywords: COINITIEE enumeration [.NET Framework metadata]
ms.assetid: 64264238-3b68-4bac-a887-36b552426a6c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 03711186954aa24beff65e5d4d5b5e484c6dc276
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="coinitiee-enumeration"></a><span data-ttu-id="4e547-102">COINITIEE 列挙型</span><span class="sxs-lookup"><span data-stu-id="4e547-102">COINITIEE Enumeration</span></span>
<span data-ttu-id="4e547-103">によって使用される定数を指定[CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)共通言語ランタイムを初期化するときにします。</span><span class="sxs-lookup"><span data-stu-id="4e547-103">Specifies constants used by [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e547-104">構文</span><span class="sxs-lookup"><span data-stu-id="4e547-104">Syntax</span></span>  
  
```  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="4e547-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="4e547-105">Members</span></span>  
  
|<span data-ttu-id="4e547-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="4e547-106">Member</span></span>|<span data-ttu-id="4e547-107">説明</span><span class="sxs-lookup"><span data-stu-id="4e547-107">Description</span></span>|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|<span data-ttu-id="4e547-108">既定の初期化モード。</span><span class="sxs-lookup"><span data-stu-id="4e547-108">Default initialization mode.</span></span> <span data-ttu-id="4e547-109">これは、ランタイムを初期化し、既定値を作成<xref:System.AppDomain>です。</span><span class="sxs-lookup"><span data-stu-id="4e547-109">This initializes the runtime and creates the default <xref:System.AppDomain>.</span></span>|  
|`COINITEE_DLL`|<span data-ttu-id="4e547-110">マネージ DLL を実行するを初期化します。</span><span class="sxs-lookup"><span data-stu-id="4e547-110">Initializes to run a managed DLL.</span></span>|  
|`COINITEE_MAIN`|<span data-ttu-id="4e547-111">マネージ EXE を実行するように初期化します。</span><span class="sxs-lookup"><span data-stu-id="4e547-111">Initializes to run a managed EXE.</span></span> <span data-ttu-id="4e547-112">これは、ランタイムを初期化しますが、既定では作成されません<xref:System.AppDomain>、これはメインの exe ファイルのルーチンを入力した後に作成します。</span><span class="sxs-lookup"><span data-stu-id="4e547-112">This initializes the runtime but does not create the default <xref:System.AppDomain>, which is created after entering the main routine of the EXE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4e547-113">要件</span><span class="sxs-lookup"><span data-stu-id="4e547-113">Requirements</span></span>  
 <span data-ttu-id="4e547-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4e547-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e547-115">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4e547-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4e547-116">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="4e547-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4e547-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e547-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e547-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="4e547-118">See Also</span></span>  
 [<span data-ttu-id="4e547-119">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="4e547-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
