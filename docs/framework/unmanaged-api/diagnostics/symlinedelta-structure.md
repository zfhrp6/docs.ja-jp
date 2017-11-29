---
title: "SYMLINEDELTA 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: SYMLINEDELTA
api_location: diasymreader.dll
api_type: COM
f1_keywords: SYMLINEDELTA
helpviewer_keywords: SYMLINEDELTA structure [.NET Framework debugging]
ms.assetid: 9634e995-d46d-4397-ab66-cc5781d11e4e
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cbd83560516e946c03a0ea71cf79fe6d3396bacb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="059fa-102">SYMLINEDELTA 構造体</span><span class="sxs-lookup"><span data-stu-id="059fa-102">SYMLINEDELTA Structure</span></span>
<span data-ttu-id="059fa-103">シンボル ハンドラーを編集した結果として移動されたメソッドに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="059fa-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="059fa-104">構文</span><span class="sxs-lookup"><span data-stu-id="059fa-104">Syntax</span></span>  
  
```  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="059fa-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="059fa-105">Members</span></span>  
  
|<span data-ttu-id="059fa-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="059fa-106">Member</span></span>|<span data-ttu-id="059fa-107">説明</span><span class="sxs-lookup"><span data-stu-id="059fa-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="059fa-108">メソッドのメタデータ トークンです。</span><span class="sxs-lookup"><span data-stu-id="059fa-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="059fa-109">メソッドが移動された行の数。</span><span class="sxs-lookup"><span data-stu-id="059fa-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="059fa-110">要件</span><span class="sxs-lookup"><span data-stu-id="059fa-110">Requirements</span></span>  
 <span data-ttu-id="059fa-111">**ヘッダー:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="059fa-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="059fa-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="059fa-112">See Also</span></span>  
 [<span data-ttu-id="059fa-113">シンボル ストア診断構造体</span><span class="sxs-lookup"><span data-stu-id="059fa-113">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
