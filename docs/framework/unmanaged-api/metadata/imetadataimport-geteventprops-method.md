---
title: IMetaDataImport::GetEventProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6ac1ecb73257782888c963082953ed243177a86b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportgeteventprops-method"></a><span data-ttu-id="fc8d9-102">IMetaDataImport::GetEventProps メソッド</span><span class="sxs-lookup"><span data-stu-id="fc8d9-102">IMetaDataImport::GetEventProps Method</span></span>
<span data-ttu-id="fc8d9-103">宣言する型、追加、デリゲートの削除メソッドと任意のフラグと関連付けられているその他のデータを含め、指定したイベント トークンによって表されるイベントのメタデータ情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="fc8d9-103">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc8d9-104">構文</span><span class="sxs-lookup"><span data-stu-id="fc8d9-104">Syntax</span></span>  
  
```  
HRESULT GetEventProps (  
   [in]  mdEvent       ev,  
   [out] mdTypeDef     *pClass,   
   [out] LPCWSTR       szEvent,   
   [in]  ULONG         cchEvent,   
   [out] ULONG         *pchEvent,   
   [out] DWORD         *pdwEventFlags,  
   [out] mdToken       *ptkEventType,  
   [out] mdMethodDef   *pmdAddOn,   
   [out] mdMethodDef   *pmdRemoveOn,   
   [out] mdMethodDef   *pmdFire,   
   [out] mdMethodDef   rmdOtherMethod[],   
   [in]  ULONG         cMax,  
   [out] ULONG         *pcOtherMethod  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc8d9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fc8d9-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="fc8d9-106">[in]メタデータを取得するイベントを表すイベントのメタデータ トークンです。</span><span class="sxs-lookup"><span data-stu-id="fc8d9-106">[in] The event metadata token representing the event to get metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="fc8d9-107">[out]イベントを宣言するクラスを表す TypeDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fc8d9-107">[out] A pointer to the TypeDef token representing the class that declares the event.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="fc8d9-108">[out]によって参照されるイベントの名前`ev`です。</span><span class="sxs-lookup"><span data-stu-id="fc8d9-108">[out] The name of the event referenced by `ev`.</span></span>  
  
 `pchEvent`  
 <span data-ttu-id="fc8d9-109">[in]要求された長さのワイド文字単位`szEvent`です。</span><span class="sxs-lookup"><span data-stu-id="fc8d9-109">[in] The requested length in wide characters of `szEvent`.</span></span>  
  
 `pdwEventFlags`  
 <span data-ttu-id="fc8d9-110">[out]ワイド文字で返される長さ`szEvent`です。</span><span class="sxs-lookup"><span data-stu-id="fc8d9-110">[out] The returned length in wide characters of `szEvent`.</span></span>  
  
 `ptkEventType`  
 <span data-ttu-id="fc8d9-111">[out]TypeRef または TypeDef メタデータ トークンを表すへのポインター、<xref:System.Delegate>イベントの種類。</span><span class="sxs-lookup"><span data-stu-id="fc8d9-111">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span></span>  
  
 `pmdAddOn`  
 <span data-ttu-id="fc8d9-112">[out]イベントのハンドラーを追加するメソッドを表すメタデータ トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fc8d9-112">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span></span>  
  
 `pmdRemoveOn`  
 <span data-ttu-id="fc8d9-113">[out]イベントのハンドラーを削除するメソッドを表すメタデータ トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fc8d9-113">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span></span>  
  
 `pmdFire`  
 <span data-ttu-id="fc8d9-114">[out]イベントを発生させるメソッドを表すメタデータ トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fc8d9-114">[out] A pointer to the metadata token representing the method that raises the event.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="fc8d9-115">[out]イベントに関連付けられたその他のメソッドへのトークンのポインターの配列。</span><span class="sxs-lookup"><span data-stu-id="fc8d9-115">[out] An array of token pointers to other methods associated with the event.</span></span>  
  
 `cMax`  
 <span data-ttu-id="fc8d9-116">[in] `rmdOtherMethod` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="fc8d9-116">[in] The maximum size of the `rmdOtherMethod` array.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="fc8d9-117">[out]返されるトークンの数`rmdOtherMethod`です。</span><span class="sxs-lookup"><span data-stu-id="fc8d9-117">[out] The number of tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc8d9-118">要件</span><span class="sxs-lookup"><span data-stu-id="fc8d9-118">Requirements</span></span>  
 <span data-ttu-id="fc8d9-119">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fc8d9-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc8d9-120">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fc8d9-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fc8d9-121">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="fc8d9-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fc8d9-122">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc8d9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc8d9-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc8d9-123">See Also</span></span>  
 [<span data-ttu-id="fc8d9-124">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fc8d9-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="fc8d9-125">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fc8d9-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
