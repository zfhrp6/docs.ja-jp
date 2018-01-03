---
title: "CreateALink 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateALink
api_location: alink.dll
api_type: DLLExport
f1_keywords: CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54a5afd8ee42fa122f3e18415be0b1d06c2f9302
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="createalink-function"></a><span data-ttu-id="a9220-102">CreateALink 関数</span><span class="sxs-lookup"><span data-stu-id="a9220-102">CreateALink Function</span></span>
<span data-ttu-id="a9220-103">アセンブリ リンカーのインスタンスを作成し、指定されたインターフェイスへのポインターを設定します。</span><span class="sxs-lookup"><span data-stu-id="a9220-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9220-104">構文</span><span class="sxs-lookup"><span data-stu-id="a9220-104">Syntax</span></span>  
  
```  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a9220-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a9220-105">Parameters</span></span>  
  
|<span data-ttu-id="a9220-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a9220-106">Parameter</span></span>|<span data-ttu-id="a9220-107">説明</span><span class="sxs-lookup"><span data-stu-id="a9220-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="a9220-108">アセンブリ リンカー インターフェイスの 1 つの物理名。</span><span class="sxs-lookup"><span data-stu-id="a9220-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="a9220-109">正常に終了へのポインターを格納する場所、`riid`インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="a9220-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a9220-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="a9220-110">Requirements</span></span>  
 <span data-ttu-id="a9220-111">**ライブラリ**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="a9220-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9220-112">参照</span><span class="sxs-lookup"><span data-stu-id="a9220-112">See Also</span></span>  
 [<span data-ttu-id="a9220-113">Al.exe (アセンブリ リンカー)</span><span class="sxs-lookup"><span data-stu-id="a9220-113">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
