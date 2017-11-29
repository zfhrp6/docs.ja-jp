---
title: "IValidator::Validate メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IValidator.Validate
api_location: mscoree.dll
api_type: COM
f1_keywords: Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 722c6acc7e152a78ba28bc2730b2fdc7e0c45eb0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ivalidatorvalidate-method"></a><span data-ttu-id="19eaa-102">IValidator::Validate メソッド</span><span class="sxs-lookup"><span data-stu-id="19eaa-102">IValidator::Validate Method</span></span>
<span data-ttu-id="19eaa-103">指定したポータブル実行可能 (PE) または Microsoft intermediate language (MSIL) ファイルを検証します。</span><span class="sxs-lookup"><span data-stu-id="19eaa-103">Validates the specified portable executable (PE) or Microsoft intermediate language (MSIL) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19eaa-104">構文</span><span class="sxs-lookup"><span data-stu-id="19eaa-104">Syntax</span></span>  
  
```  
HRESULT Validate (  
    [in] IVEHandler            *veh,  
    [in] IUnknown              *pAppDomain,  
    [in] unsigned long          ulFlags,  
    [in] unsigned long          ulMaxError,  
    [in] unsigned long          token,  
    [in] LPWSTR                 fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long          ulSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="19eaa-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="19eaa-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="19eaa-106">[in]ポインター、`IVEHandler`妥当性確認エラーを処理するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="19eaa-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="19eaa-107">[in]ファイルが読み込まれているアプリケーション ドメインへのポインター。</span><span class="sxs-lookup"><span data-stu-id="19eaa-107">[in] A pointer to the application domain in which the file is loaded.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="19eaa-108">[in]ビットごとの組み合わせ[ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md)を実行するか、検証を示す値。</span><span class="sxs-lookup"><span data-stu-id="19eaa-108">[in] A bitwise combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the validations that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="19eaa-109">[in]検証を終了する前に許可されるエラーの最大数。</span><span class="sxs-lookup"><span data-stu-id="19eaa-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="19eaa-110">[in]使用しません。</span><span class="sxs-lookup"><span data-stu-id="19eaa-110">[in] Not used.</span></span>  
  
 `fileName`  
 <span data-ttu-id="19eaa-111">[in]検証に使用するファイルの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="19eaa-111">[in] A string that specifies the name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="19eaa-112">[in]ファイルが格納されているメモリ バッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="19eaa-112">[in] A pointer to the memory buffer in which the file is stored.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="19eaa-113">[in]検証に使用するファイルのバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="19eaa-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19eaa-114">要件</span><span class="sxs-lookup"><span data-stu-id="19eaa-114">Requirements</span></span>  
 <span data-ttu-id="19eaa-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="19eaa-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19eaa-116">**ヘッダー:** IValidator.idl、IValidator.h</span><span class="sxs-lookup"><span data-stu-id="19eaa-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="19eaa-117">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="19eaa-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19eaa-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19eaa-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19eaa-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="19eaa-119">See Also</span></span>  
 
