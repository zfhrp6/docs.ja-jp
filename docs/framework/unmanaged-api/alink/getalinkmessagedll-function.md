---
title: "GetALinkMessageDll 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- GetALinkMessageDll
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- GetALinkMessageDll
helpviewer_keywords:
- Alink API, GetALinkMessageDll function
- GetALinkMessageDll function
ms.assetid: 67985a22-88a2-4c54-8d99-4bcde9d6213e
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 16657c62d66db1570ad379ff5d42a75aaf3ea2a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="b06b0-102">GetALinkMessageDll 関数</span><span class="sxs-lookup"><span data-stu-id="b06b0-102">GetALinkMessageDll Function</span></span>
<span data-ttu-id="b06b0-103">検索し、メッセージ DLL を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="b06b0-103">Finds and loads the message DLL.</span></span> <span data-ttu-id="b06b0-104">メッセージ DLL があるか、読み込まれた場合は、0 を返します。</span><span class="sxs-lookup"><span data-stu-id="b06b0-104">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="b06b0-105">メッセージ DLL は、その名前は、言語 ID、名前のサブディレクトリに、または現在のディレクトリにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b06b0-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b06b0-106">構文</span><span class="sxs-lookup"><span data-stu-id="b06b0-106">Syntax</span></span>  
  
```  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="b06b0-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="b06b0-107">Requirements</span></span>  
 <span data-ttu-id="b06b0-108">**ヘッダー:** alink.h</span><span class="sxs-lookup"><span data-stu-id="b06b0-108">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="b06b0-109">**ライブラリ**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="b06b0-109">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b06b0-110">参照</span><span class="sxs-lookup"><span data-stu-id="b06b0-110">See Also</span></span>  
 [<span data-ttu-id="b06b0-111">Al.exe (アセンブリ リンカー)</span><span class="sxs-lookup"><span data-stu-id="b06b0-111">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
