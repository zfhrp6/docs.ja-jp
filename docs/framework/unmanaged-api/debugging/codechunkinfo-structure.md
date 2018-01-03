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
ms.workload: dotnet
ms.openlocfilehash: d7b3b858d645f01f58ba0b67465b22dd05282656
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="codechunkinfo-structure1"></a><span data-ttu-id="2f249-102">CodeChunkInfo Structure1</span><span class="sxs-lookup"><span data-stu-id="2f249-102">CodeChunkInfo Structure1</span></span>
<span data-ttu-id="2f249-103">メモリ内のコードの単一のチャンクを表しています。</span><span class="sxs-lookup"><span data-stu-id="2f249-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f249-104">構文</span><span class="sxs-lookup"><span data-stu-id="2f249-104">Syntax</span></span>  
  
```  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="2f249-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f249-105">Members</span></span>  
  
|<span data-ttu-id="2f249-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="2f249-106">Member</span></span>|<span data-ttu-id="2f249-107">説明</span><span class="sxs-lookup"><span data-stu-id="2f249-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="2f249-108">A`CORDB_ADDRESS`チャンクの開始アドレスを指定する値。</span><span class="sxs-lookup"><span data-stu-id="2f249-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="2f249-109">チャンクのバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="2f249-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f249-110">コメント</span><span class="sxs-lookup"><span data-stu-id="2f249-110">Remarks</span></span>  
 <span data-ttu-id="2f249-111">コードの単一のチャンクは、関数などのコード オブジェクトの一部であるネイティブ コードの領域です。</span><span class="sxs-lookup"><span data-stu-id="2f249-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f249-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="2f249-112">Requirements</span></span>  
 <span data-ttu-id="2f249-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f249-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f249-114">**ヘッダー:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="2f249-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="2f249-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f249-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f249-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f249-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f249-117">参照</span><span class="sxs-lookup"><span data-stu-id="2f249-117">See Also</span></span>  
 [<span data-ttu-id="2f249-118">GetCodeChunks メソッド</span><span class="sxs-lookup"><span data-stu-id="2f249-118">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)  
 [<span data-ttu-id="2f249-119">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="2f249-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="2f249-120">デバッグ</span><span class="sxs-lookup"><span data-stu-id="2f249-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
