---
title: "IMetaDataImport2::GetVersionString メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.GetVersionString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d08f43a790305c960d557064539de680a2d04af9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2getversionstring-method"></a><span data-ttu-id="f0f22-102">IMetaDataImport2::GetVersionString メソッド</span><span class="sxs-lookup"><span data-stu-id="f0f22-102">IMetaDataImport2::GetVersionString Method</span></span>
<span data-ttu-id="f0f22-103">アセンブリをビルドするために使用されたランタイムのバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="f0f22-103">Gets the version number of the runtime that was used to build the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0f22-104">構文</span><span class="sxs-lookup"><span data-stu-id="f0f22-104">Syntax</span></span>  
  
```  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f0f22-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f0f22-105">Parameters</span></span>  
 `pwzBuf`  
 <span data-ttu-id="f0f22-106">[out]バージョンを指定する文字列を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="f0f22-106">[out] An array to store the string that specifies the version.</span></span>  
  
 `ccBufSize`  
 <span data-ttu-id="f0f22-107">[in]ワイド文字単位のサイズの`pwzBuf`配列。</span><span class="sxs-lookup"><span data-stu-id="f0f22-107">[in] The size, in wide characters, of the `pwzBuf` array.</span></span>  
  
 `pccBufSize`  
 <span data-ttu-id="f0f22-108">[out]Null 終端文字を含む、ワイド文字の数が返される、`pwzBuf`配列。</span><span class="sxs-lookup"><span data-stu-id="f0f22-108">[out] The number of wide characters, including a null terminator, returned in the `pwzBuf` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0f22-109">コメント</span><span class="sxs-lookup"><span data-stu-id="f0f22-109">Remarks</span></span>  
 <span data-ttu-id="f0f22-110">`GetVersionString`メソッドは、現在のメタデータ スコープのビルドのバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="f0f22-110">The `GetVersionString` method gets the built-for version of the current metadata scope.</span></span> <span data-ttu-id="f0f22-111">スコープが保存されていない場合ビルドのバージョンはありませんし、空の文字列が返されます。</span><span class="sxs-lookup"><span data-stu-id="f0f22-111">If the scope has never been saved, it will not have a built-for version, and an empty string will be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0f22-112">要件</span><span class="sxs-lookup"><span data-stu-id="f0f22-112">Requirements</span></span>  
 <span data-ttu-id="f0f22-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f0f22-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0f22-114">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f0f22-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f0f22-115">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="f0f22-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f0f22-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0f22-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0f22-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="f0f22-117">See Also</span></span>  
 [<span data-ttu-id="f0f22-118">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f0f22-118">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="f0f22-119">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f0f22-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
