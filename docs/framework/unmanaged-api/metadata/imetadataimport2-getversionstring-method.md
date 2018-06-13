---
title: IMetaDataImport2::GetVersionString メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 112ddcf51a5637bb89df9479850c2a4a70d2e1d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448727"
---
# <a name="imetadataimport2getversionstring-method"></a><span data-ttu-id="ca7bb-102">IMetaDataImport2::GetVersionString メソッド</span><span class="sxs-lookup"><span data-stu-id="ca7bb-102">IMetaDataImport2::GetVersionString Method</span></span>
<span data-ttu-id="ca7bb-103">アセンブリをビルドするために使用されたランタイムのバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="ca7bb-103">Gets the version number of the runtime that was used to build the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca7bb-104">構文</span><span class="sxs-lookup"><span data-stu-id="ca7bb-104">Syntax</span></span>  
  
```  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ca7bb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ca7bb-105">Parameters</span></span>  
 `pwzBuf`  
 <span data-ttu-id="ca7bb-106">[out]バージョンを指定する文字列を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="ca7bb-106">[out] An array to store the string that specifies the version.</span></span>  
  
 `ccBufSize`  
 <span data-ttu-id="ca7bb-107">[in]ワイド文字単位のサイズの`pwzBuf`配列。</span><span class="sxs-lookup"><span data-stu-id="ca7bb-107">[in] The size, in wide characters, of the `pwzBuf` array.</span></span>  
  
 `pccBufSize`  
 <span data-ttu-id="ca7bb-108">[out]Null 終端文字を含む、ワイド文字の数が返される、`pwzBuf`配列。</span><span class="sxs-lookup"><span data-stu-id="ca7bb-108">[out] The number of wide characters, including a null terminator, returned in the `pwzBuf` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca7bb-109">コメント</span><span class="sxs-lookup"><span data-stu-id="ca7bb-109">Remarks</span></span>  
 <span data-ttu-id="ca7bb-110">`GetVersionString`メソッドは、現在のメタデータ スコープのビルドのバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="ca7bb-110">The `GetVersionString` method gets the built-for version of the current metadata scope.</span></span> <span data-ttu-id="ca7bb-111">スコープが保存されていない場合ビルドのバージョンはありませんし、空の文字列が返されます。</span><span class="sxs-lookup"><span data-stu-id="ca7bb-111">If the scope has never been saved, it will not have a built-for version, and an empty string will be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca7bb-112">要件</span><span class="sxs-lookup"><span data-stu-id="ca7bb-112">Requirements</span></span>  
 <span data-ttu-id="ca7bb-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca7bb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca7bb-114">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ca7bb-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ca7bb-115">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="ca7bb-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ca7bb-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca7bb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca7bb-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="ca7bb-117">See Also</span></span>  
 [<span data-ttu-id="ca7bb-118">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ca7bb-118">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="ca7bb-119">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ca7bb-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
