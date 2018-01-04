---
title: "IMapToken::Map メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMapToken.Map
api_location: mscoree.dll
api_type: COM
f1_keywords: IMapToken::Map
helpviewer_keywords:
- IMapToken::Map method [.NET Framework metadata]
- Map method [.NET Framework metadata]
ms.assetid: b9b4bf2f-1098-43d6-9619-a99b4bda1940
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fe034d2bc6d70e820fa3ad5de8140afa9a19a6bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imaptokenmap-method"></a><span data-ttu-id="c45fd-102">IMapToken::Map メソッド</span><span class="sxs-lookup"><span data-stu-id="c45fd-102">IMapToken::Map Method</span></span>
<span data-ttu-id="c45fd-103">メタデータ署名を使用してアセンブリ間の関係をマップします。</span><span class="sxs-lookup"><span data-stu-id="c45fd-103">Maps a relationship between the assemblies using metadata signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c45fd-104">構文</span><span class="sxs-lookup"><span data-stu-id="c45fd-104">Syntax</span></span>  
  
```  
HRESULT Map (  
    [in]  mdToken tkImp,   
    [in]  mdToken tkEmit  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c45fd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c45fd-105">Parameters</span></span>  
 `tkImp`  
 <span data-ttu-id="c45fd-106">[in]インポートしたコード オブジェクトを表すメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="c45fd-106">[in] The metadata token that represents the imported code object.</span></span>  
  
 `tkEmit`  
 <span data-ttu-id="c45fd-107">[in]出力コード オブジェクトを表すメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="c45fd-107">[in] The metadata token that represents the emitted code object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c45fd-108">コメント</span><span class="sxs-lookup"><span data-stu-id="c45fd-108">Remarks</span></span>  
 <span data-ttu-id="c45fd-109">トークンの再マップ発生すると、マージ中には、元のトークンがインポートされた (ソース) のメタデータ スコープ内スコープが設定され、新しいトークンが生成された (ターゲット) のメタデータ スコープにスコープが設定します。</span><span class="sxs-lookup"><span data-stu-id="c45fd-109">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c45fd-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="c45fd-110">Requirements</span></span>  
 <span data-ttu-id="c45fd-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c45fd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c45fd-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c45fd-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c45fd-113">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="c45fd-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c45fd-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c45fd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c45fd-115">参照</span><span class="sxs-lookup"><span data-stu-id="c45fd-115">See Also</span></span>  
 [<span data-ttu-id="c45fd-116">IMapToken インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c45fd-116">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
