---
title: GetALinkMessageDll 関数
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 395dc85ad638e8a790962a4aa38019612c360ce1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402218"
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="b97b1-102">GetALinkMessageDll 関数</span><span class="sxs-lookup"><span data-stu-id="b97b1-102">GetALinkMessageDll Function</span></span>
<span data-ttu-id="b97b1-103">検索し、メッセージ DLL を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="b97b1-103">Finds and loads the message DLL.</span></span> <span data-ttu-id="b97b1-104">メッセージ DLL があるか、読み込まれた場合は、0 を返します。</span><span class="sxs-lookup"><span data-stu-id="b97b1-104">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="b97b1-105">メッセージ DLL は、その名前は、言語 ID、名前のサブディレクトリに、または現在のディレクトリにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b97b1-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b97b1-106">構文</span><span class="sxs-lookup"><span data-stu-id="b97b1-106">Syntax</span></span>  
  
```  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="b97b1-107">要件</span><span class="sxs-lookup"><span data-stu-id="b97b1-107">Requirements</span></span>  
 <span data-ttu-id="b97b1-108">**ヘッダー:** alink.h</span><span class="sxs-lookup"><span data-stu-id="b97b1-108">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="b97b1-109">**ライブラリ**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="b97b1-109">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b97b1-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="b97b1-110">See Also</span></span>  
 [<span data-ttu-id="b97b1-111">Al.exe (アセンブリ リンカー)</span><span class="sxs-lookup"><span data-stu-id="b97b1-111">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
