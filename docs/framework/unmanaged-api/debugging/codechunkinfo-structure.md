---
title: CodeChunkInfo Structure1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CodeChunkInfo
api_location: mscordbi.dll
api_type: COM
f1_keywords: CodeChunkInfo
helpviewer_keywords: CodeChunkInfo structure [.NET Framework debugging]
ms.assetid: 0f482454-8517-48de-ba7a-d7aedab13bb5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 17727c8927f9db3de3ab26d2504dfae5215a1495
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="codechunkinfo-structure1"></a><span data-ttu-id="ba2b0-102">CodeChunkInfo Structure1</span><span class="sxs-lookup"><span data-stu-id="ba2b0-102">CodeChunkInfo Structure1</span></span>
<span data-ttu-id="ba2b0-103">メモリ内のコードの単一のチャンクを表しています。</span><span class="sxs-lookup"><span data-stu-id="ba2b0-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba2b0-104">構文</span><span class="sxs-lookup"><span data-stu-id="ba2b0-104">Syntax</span></span>  
  
```  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="ba2b0-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="ba2b0-105">Members</span></span>  
  
|<span data-ttu-id="ba2b0-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="ba2b0-106">Member</span></span>|<span data-ttu-id="ba2b0-107">説明</span><span class="sxs-lookup"><span data-stu-id="ba2b0-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="ba2b0-108">A`CORDB_ADDRESS`チャンクの開始アドレスを指定する値。</span><span class="sxs-lookup"><span data-stu-id="ba2b0-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="ba2b0-109">チャンクのバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="ba2b0-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba2b0-110">コメント</span><span class="sxs-lookup"><span data-stu-id="ba2b0-110">Remarks</span></span>  
 <span data-ttu-id="ba2b0-111">コードの単一のチャンクは、関数などのコード オブジェクトの一部であるネイティブ コードの領域です。</span><span class="sxs-lookup"><span data-stu-id="ba2b0-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba2b0-112">要件</span><span class="sxs-lookup"><span data-stu-id="ba2b0-112">Requirements</span></span>  
 <span data-ttu-id="ba2b0-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ba2b0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba2b0-114">**ヘッダー:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="ba2b0-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="ba2b0-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba2b0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba2b0-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba2b0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba2b0-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="ba2b0-117">See Also</span></span>  
 [<span data-ttu-id="ba2b0-118">GetCodeChunks メソッド</span><span class="sxs-lookup"><span data-stu-id="ba2b0-118">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)  
 [<span data-ttu-id="ba2b0-119">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="ba2b0-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="ba2b0-120">デバッグ</span><span class="sxs-lookup"><span data-stu-id="ba2b0-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
