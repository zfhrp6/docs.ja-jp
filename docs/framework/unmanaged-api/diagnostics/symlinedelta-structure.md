---
title: SYMLINEDELTA 構造体
ms.date: 03/30/2017
api_name:
- SYMLINEDELTA
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SYMLINEDELTA
helpviewer_keywords:
- SYMLINEDELTA structure [.NET Framework debugging]
ms.assetid: 9634e995-d46d-4397-ab66-cc5781d11e4e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 77cd8b7d791d11f6d40386f4747c60cd4832521a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428095"
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="d8659-102">SYMLINEDELTA 構造体</span><span class="sxs-lookup"><span data-stu-id="d8659-102">SYMLINEDELTA Structure</span></span>
<span data-ttu-id="d8659-103">シンボル ハンドラーを編集した結果として移動されたメソッドに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="d8659-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8659-104">構文</span><span class="sxs-lookup"><span data-stu-id="d8659-104">Syntax</span></span>  
  
```  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="d8659-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="d8659-105">Members</span></span>  
  
|<span data-ttu-id="d8659-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="d8659-106">Member</span></span>|<span data-ttu-id="d8659-107">説明</span><span class="sxs-lookup"><span data-stu-id="d8659-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="d8659-108">メソッドのメタデータ トークンです。</span><span class="sxs-lookup"><span data-stu-id="d8659-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="d8659-109">メソッドが移動された行の数。</span><span class="sxs-lookup"><span data-stu-id="d8659-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d8659-110">要件</span><span class="sxs-lookup"><span data-stu-id="d8659-110">Requirements</span></span>  
 <span data-ttu-id="d8659-111">**ヘッダー:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="d8659-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8659-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="d8659-112">See Also</span></span>  
 [<span data-ttu-id="d8659-113">シンボル ストア診断構造体</span><span class="sxs-lookup"><span data-stu-id="d8659-113">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
