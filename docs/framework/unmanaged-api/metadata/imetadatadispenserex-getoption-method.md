---
title: "IMetaDataDispenserEx::GetOption メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.GetOption
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::GetOption
helpviewer_keywords:
- GetOption method [.NET Framework metadata]
- IMetaDataDispenserEx::GetOption method [.NET Framework metadata]
ms.assetid: d7f794e5-8e25-4d65-850a-7c34fbfce87d
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fa9db222c81c2d6536b782c3e047e24c773bd018
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="12238-102">IMetaDataDispenserEx::GetOption メソッド</span><span class="sxs-lookup"><span data-stu-id="12238-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="12238-103">現在のメタデータ スコープに指定されたオプションの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="12238-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="12238-104">オプションは、現在のメタデータ スコープへの呼び出しの処理方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="12238-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12238-105">構文</span><span class="sxs-lookup"><span data-stu-id="12238-105">Syntax</span></span>  
  
```  
HRESULT GetOption (  
    [in]  REFGUID         optionId,   
    [out] const VARIANT   *pValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="12238-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="12238-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="12238-107">[in]取得するオプションを指定する GUID を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="12238-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="12238-108">サポートされている Guid の一覧については、「解説」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="12238-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="12238-109">[out]返されるオプションの値。</span><span class="sxs-lookup"><span data-stu-id="12238-109">[out] The value of the returned option.</span></span> <span data-ttu-id="12238-110">この値の型は、指定したオプションの種類のバリアント型になります。</span><span class="sxs-lookup"><span data-stu-id="12238-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12238-111">コメント</span><span class="sxs-lookup"><span data-stu-id="12238-111">Remarks</span></span>  
 <span data-ttu-id="12238-112">次の一覧は、このメソッドがサポートされている Guid を示しています。</span><span class="sxs-lookup"><span data-stu-id="12238-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="12238-113">詳細については、次を参照してください。、 [imetadatadispenserex::setoption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="12238-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="12238-114">場合`optionId`はこの一覧にないは、このメソッドは HRESULT を返します。 `E_INVALIDARG`、無効なパラメーターを示すです。</span><span class="sxs-lookup"><span data-stu-id="12238-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
-   <span data-ttu-id="12238-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="12238-115">MetaDataCheckDuplicatesFor</span></span>  
  
-   <span data-ttu-id="12238-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="12238-116">MetaDataRefToDefCheck</span></span>  
  
-   <span data-ttu-id="12238-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="12238-117">MetaDataNotificationForTokenMovement</span></span>  
  
-   <span data-ttu-id="12238-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="12238-118">MetaDataSetENC</span></span>  
  
-   <span data-ttu-id="12238-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="12238-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
-   <span data-ttu-id="12238-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="12238-120">MetaDataGenerateTCEAdapters</span></span>  
  
-   <span data-ttu-id="12238-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="12238-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12238-122">要件</span><span class="sxs-lookup"><span data-stu-id="12238-122">Requirements</span></span>  
 <span data-ttu-id="12238-123">**Platform:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="12238-123">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12238-124">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="12238-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="12238-125">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="12238-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="12238-126">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12238-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12238-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="12238-127">See Also</span></span>  
 [<span data-ttu-id="12238-128">IMetaDataDispenserEx インターフェイス</span><span class="sxs-lookup"><span data-stu-id="12238-128">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="12238-129">IMetaDataDispenser インターフェイス</span><span class="sxs-lookup"><span data-stu-id="12238-129">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
