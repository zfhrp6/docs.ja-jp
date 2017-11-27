---
title: "IMetaDataValidate::ValidatorInit メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataValidate.ValidatorInit
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataValidate::ValidatorInit
helpviewer_keywords:
- IMetaDataValidate::ValidatorInit method [.NET Framework metadata]
- ValidatorInit method [.NET Framework metadata]
ms.assetid: 6bafd75a-e2d0-4aea-aed1-074374d5dff6
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e2a9b265b4fcc75406f5d5f1dbddb8bd74b5832d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="imetadatavalidatevalidatorinit-method"></a><span data-ttu-id="ac5be-102">IMetaDataValidate::ValidatorInit メソッド</span><span class="sxs-lookup"><span data-stu-id="ac5be-102">IMetaDataValidate::ValidatorInit Method</span></span>
<span data-ttu-id="ac5be-103">現在のメタデータ スコープ内にあるモジュールの種類を指定するフラグを設定し、指定されたコールバック メソッドを検証エラー用に登録します。</span><span class="sxs-lookup"><span data-stu-id="ac5be-103">Sets a flag that specifies the type of the module in the current metadata scope, and registers the specified callback method for validation errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac5be-104">構文</span><span class="sxs-lookup"><span data-stu-id="ac5be-104">Syntax</span></span>  
  
```  
HRESULT ValidatorInit (  
   [in] DWORD       dwModuleType,  
   [in] IUnknown    *pUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ac5be-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ac5be-105">Parameters</span></span>  
 `dwModule`  
 <span data-ttu-id="ac5be-106">[in]値、 [CorValidatorModuleType](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md)の現在のメタデータ スコープ内のモジュールの種類を指定する列挙体です。</span><span class="sxs-lookup"><span data-stu-id="ac5be-106">[in] A value of the [CorValidatorModuleType](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md) enumeration that specifies the type of the module in the current metadata scope.</span></span>  
  
 `pUnk`  
 <span data-ttu-id="ac5be-107">[in]ポインターを <<!--zzxref:IUnknown --> `IUnknown`> 妥当性確認エラーのコールバックで関数として機能するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="ac5be-107">[in] A pointer to an <<!--zzxref:IUnknown --> `IUnknown`> instance that serves as a function callback for validation errors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac5be-108">要件</span><span class="sxs-lookup"><span data-stu-id="ac5be-108">Requirements</span></span>  
 <span data-ttu-id="ac5be-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ac5be-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac5be-110">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ac5be-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ac5be-111">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="ac5be-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ac5be-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac5be-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac5be-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac5be-113">See Also</span></span>  
 [<span data-ttu-id="ac5be-114">IMetaDataValidate インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ac5be-114">IMetaDataValidate Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)
