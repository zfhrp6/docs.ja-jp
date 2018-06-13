---
title: IMetaDataEmit::SetHandler メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetHandler
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetHandler
helpviewer_keywords:
- IMetaDataEmit::SetHandler method [.NET Framework metadata]
- SetHandler method [.NET Framework metadata]
ms.assetid: c6c1aaaf-e2cd-407c-b73e-fbe6ffd83bb3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 60c9266806ef6b5d7e2e1c3a219a4485bc22d7f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445521"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="ca27a-102">IMetaDataEmit::SetHandler メソッド</span><span class="sxs-lookup"><span data-stu-id="ca27a-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="ca27a-103">指定したによって参照されるメソッドを設定`IUnknown`トークンを再マップの通知のコールバックとしてのポインター。</span><span class="sxs-lookup"><span data-stu-id="ca27a-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca27a-104">構文</span><span class="sxs-lookup"><span data-stu-id="ca27a-104">Syntax</span></span>  
  
```  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ca27a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ca27a-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="ca27a-106">[in]登録するハンドラー。</span><span class="sxs-lookup"><span data-stu-id="ca27a-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca27a-107">コメント</span><span class="sxs-lookup"><span data-stu-id="ca27a-107">Remarks</span></span>  
 <span data-ttu-id="ca27a-108">メタデータ エンジンによって提供されるメソッドを使用して通知を送信する`SetHandler`コンパイラが最適化された方法でレコードが生成されないことをしたいと考えて保存されているレコードを最適化します。</span><span class="sxs-lookup"><span data-stu-id="ca27a-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="ca27a-109">を介して、コールバック メソッドが指定されていない場合`SetHandler`、最適化は実行されませんで保存さまざまなインポートを除くスコープがマージされたを使用して`IMapToken`スコープごとにマージにします。</span><span class="sxs-lookup"><span data-stu-id="ca27a-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca27a-110">要件</span><span class="sxs-lookup"><span data-stu-id="ca27a-110">Requirements</span></span>  
 <span data-ttu-id="ca27a-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca27a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca27a-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ca27a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ca27a-113">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="ca27a-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca27a-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca27a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca27a-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ca27a-115">See Also</span></span>  
 [<span data-ttu-id="ca27a-116">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ca27a-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="ca27a-117">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ca27a-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
