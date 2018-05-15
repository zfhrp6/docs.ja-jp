---
title: COR_IL_MAP 構造体
ms.date: 03/30/2017
api_name:
- COR_IL_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_IL_MAP
helpviewer_keywords:
- COR_IL_MAP structure [.NET Framework debugging]
ms.assetid: 534ebc17-963d-4b26-8375-8cd940281db3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9676730a4f11ed77996b7a4aab4e538aba9b53c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="corilmap-structure"></a><span data-ttu-id="49275-102">COR_IL_MAP 構造体</span><span class="sxs-lookup"><span data-stu-id="49275-102">COR_IL_MAP Structure</span></span>
<span data-ttu-id="49275-103">機能の相対オフセットでの変更を指定します。</span><span class="sxs-lookup"><span data-stu-id="49275-103">Specifies changes in the relative offset of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49275-104">構文</span><span class="sxs-lookup"><span data-stu-id="49275-104">Syntax</span></span>  
  
```  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="49275-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="49275-105">Members</span></span>  
  
|<span data-ttu-id="49275-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="49275-106">Member</span></span>|<span data-ttu-id="49275-107">説明</span><span class="sxs-lookup"><span data-stu-id="49275-107">Description</span></span>|  
|------------|-----------------|  
|`oldOffset`|<span data-ttu-id="49275-108">古い Microsoft intermediate language (MSIL) 関数の先頭からの相対オフセットします。</span><span class="sxs-lookup"><span data-stu-id="49275-108">The old Microsoft intermediate language (MSIL) offset relative to the beginning of the function.</span></span>|  
|`newOffset`|<span data-ttu-id="49275-109">関数の先頭からの相対新しい MSIL オフセットします。</span><span class="sxs-lookup"><span data-stu-id="49275-109">The new MSIL offset relative to the beginning of the function.</span></span>|  
|`fAccurate`|<span data-ttu-id="49275-110">`true` マッピングは正確である既知の場合それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="49275-110">`true` if the mapping is known to be accurate; otherwise, `false`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49275-111">コメント</span><span class="sxs-lookup"><span data-stu-id="49275-111">Remarks</span></span>  
 <span data-ttu-id="49275-112">マップの形式は次のように、: デバッガーと見なされます`oldOffset`、元の未変更の MSIL コード内の MSIL オフセットを参照します。</span><span class="sxs-lookup"><span data-stu-id="49275-112">The format of the map is as follows: The debugger will assume that `oldOffset` refers to an MSIL offset within the original, unmodified MSIL code.</span></span> <span data-ttu-id="49275-113">`newOffset`パラメーターは、新しいでインストルメント化されたコード内の対応する MSIL オフセットを表します。</span><span class="sxs-lookup"><span data-stu-id="49275-113">The `newOffset` parameter refers to the corresponding MSIL offset within the new, instrumented code.</span></span>  
  
 <span data-ttu-id="49275-114">正常に動作する、ステップの次の要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="49275-114">For stepping to work properly, the following requirements should be met:</span></span>  
  
-   <span data-ttu-id="49275-115">マップは、昇順で並べ替えする必要があります。</span><span class="sxs-lookup"><span data-stu-id="49275-115">The map should be sorted in ascending order.</span></span>  
  
-   <span data-ttu-id="49275-116">インストルメント化された MSIL コードは並べ替えないでください。</span><span class="sxs-lookup"><span data-stu-id="49275-116">Instrumented MSIL code should not be reordered.</span></span>  
  
-   <span data-ttu-id="49275-117">元の MSIL コードを削除してはなりません。</span><span class="sxs-lookup"><span data-stu-id="49275-117">Original MSIL code should not be removed.</span></span>  
  
-   <span data-ttu-id="49275-118">マップには、プログラム データベース (PDB) ファイルからのすべてのシーケンス ポイントをマップするエントリを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="49275-118">The map should include entries to map all the sequence points from the program database (PDB) file.</span></span>  
  
 <span data-ttu-id="49275-119">存在しないエントリを補間、マップは行いません。</span><span class="sxs-lookup"><span data-stu-id="49275-119">The map does not interpolate missing entries.</span></span> <span data-ttu-id="49275-120">次の例では、マップとその結果を示します。</span><span class="sxs-lookup"><span data-stu-id="49275-120">The following example shows a map and its results.</span></span>  
  
 <span data-ttu-id="49275-121">マップ:</span><span class="sxs-lookup"><span data-stu-id="49275-121">Map:</span></span>  
  
-   <span data-ttu-id="49275-122">古いオフセットが 0、0 の新しいオフセット</span><span class="sxs-lookup"><span data-stu-id="49275-122">0 old offset, 0 new offset</span></span>  
  
-   <span data-ttu-id="49275-123">古いオフセットが 5、10 個の新しいオフセット</span><span class="sxs-lookup"><span data-stu-id="49275-123">5 old offset, 10 new offset</span></span>  
  
-   <span data-ttu-id="49275-124">古いオフセットを 9、20 の新しいオフセット</span><span class="sxs-lookup"><span data-stu-id="49275-124">9 old offset, 20 new offset</span></span>  
  
 <span data-ttu-id="49275-125">結果:</span><span class="sxs-lookup"><span data-stu-id="49275-125">Results:</span></span>  
  
-   <span data-ttu-id="49275-126">古いオフセットが 0、1、2、3、または 4 は、新しいオフセット 0 にマップされます。</span><span class="sxs-lookup"><span data-stu-id="49275-126">An old offset of 0, 1, 2, 3, or 4 will be mapped to a new offset of 0.</span></span>  
  
-   <span data-ttu-id="49275-127">古いオフセットが 5、6、7、または 8 は、新しいオフセット 10 にマップされます。</span><span class="sxs-lookup"><span data-stu-id="49275-127">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
-   <span data-ttu-id="49275-128">9 以降の古いオフセットは、新しいオフセット 20 にマップされます。</span><span class="sxs-lookup"><span data-stu-id="49275-128">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
-   <span data-ttu-id="49275-129">0、1、2、3、4、5、6、7、8、または 9 の新しいオフセットは、古いオフセット 0 にマップされます。</span><span class="sxs-lookup"><span data-stu-id="49275-129">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
-   <span data-ttu-id="49275-130">10、11、12、13、14、15、16、17、18 または 19 の新しいオフセットは、古いオフセット 5 にマップされます。</span><span class="sxs-lookup"><span data-stu-id="49275-130">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
-   <span data-ttu-id="49275-131">20 以上の新しいオフセットは、古いオフセット 9 にマップされます。</span><span class="sxs-lookup"><span data-stu-id="49275-131">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49275-132">要件</span><span class="sxs-lookup"><span data-stu-id="49275-132">Requirements</span></span>  
 <span data-ttu-id="49275-133">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="49275-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49275-134">**ヘッダー:** CorDebug.idl、CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="49275-134">**Header:** CorDebug.idl, CorProf.idl</span></span>  
  
 <span data-ttu-id="49275-135">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49275-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49275-136">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49275-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49275-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="49275-137">See Also</span></span>  
 [<span data-ttu-id="49275-138">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="49275-138">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="49275-139">デバッグ</span><span class="sxs-lookup"><span data-stu-id="49275-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
