---
title: "ValidatorFlags 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ValidatorFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ValidatorFlags
helpviewer_keywords:
- ValidatorFlags enumeration [.NET Framework hosting]
ms.assetid: a3f5c266-3fcc-4ad1-aaf5-4cdbe26304ad
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 952944e9ae9a8186a182796deb587b6fa6a0d6a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="validatorflags-enumeration"></a><span data-ttu-id="6af1d-102">ValidatorFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="6af1d-102">ValidatorFlags Enumeration</span></span>
<span data-ttu-id="6af1d-103">呼び出しで実行される検証の種類を示す値を含む、 [iclrvalidator::validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="6af1d-103">Contains values that indicate the type of validation that should be performed in a call to the [ICLRValidator::Validate](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6af1d-104">構文</span><span class="sxs-lookup"><span data-stu-id="6af1d-104">Syntax</span></span>  
  
```  
enum ValidatorFlags {  
    VALIDATOR_EXTRA_VERBOSE =       0x00000001,  
    VALIDATOR_SHOW_SOURCE_LINES =   0x00000002,  
    VALIDATOR_CHECK_ILONLY =        0x00000004,  
    VALIDATOR_CHECK_PEFORMAT_ONLY = 0x00000008,  
    VALIDATOR_NOCHECK_PEFORMAT =    0x00000010,  
};  
```  
  
## <a name="members"></a><span data-ttu-id="6af1d-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="6af1d-105">Members</span></span>  
  
|<span data-ttu-id="6af1d-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="6af1d-106">Member</span></span>|<span data-ttu-id="6af1d-107">説明</span><span class="sxs-lookup"><span data-stu-id="6af1d-107">Description</span></span>|  
|------------|-----------------|  
|`VALIDATOR_CHECK_ILONLY`|<span data-ttu-id="6af1d-108">のみ Microsoft intermediate language (MSIL)、実行可能ファイルを検証することを指定します。</span><span class="sxs-lookup"><span data-stu-id="6af1d-108">Specifies that only the Microsoft intermediate language (MSIL) in the executable file should be validated.</span></span>|  
|`VALIDATOR_CHECK_PEFORMAT_ONLY`|<span data-ttu-id="6af1d-109">実行可能ファイルの形式に関するのみを検証することを指定します。</span><span class="sxs-lookup"><span data-stu-id="6af1d-109">Specifies that only the format of the executable file should be validated.</span></span>|  
|`VALIDATOR_EXTRA_VERBOSE`|<span data-ttu-id="6af1d-110">すべての種類の検証を実行ありで報告されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="6af1d-110">Specifies that all types of validation should be performed and reported on.</span></span>|  
|`VALIDATOR_NOCHECK_PEFORMAT`|<span data-ttu-id="6af1d-111">実行可能ファイルの形式を検証しないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="6af1d-111">Specifies that the format of the executable file should not be validated.</span></span>|  
|`VALIDATOR_SHOW_SOURCE_LINES`|<span data-ttu-id="6af1d-112">検証エラー メッセージが検証エラーが発生するソース コードの行を含める必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="6af1d-112">Specifies that validation error messages should include the lines of source code that raise validation errors.</span></span> <span data-ttu-id="6af1d-113">.NET Framework version 2.0 でこのフィールドの値が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="6af1d-113">This field value is not valid in the .NET Framework version 2.0.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6af1d-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="6af1d-114">Requirements</span></span>  
 <span data-ttu-id="6af1d-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6af1d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6af1d-116">**ヘッダー:** IValidator.idl、IValidator.h</span><span class="sxs-lookup"><span data-stu-id="6af1d-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="6af1d-117">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6af1d-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6af1d-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6af1d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6af1d-119">参照</span><span class="sxs-lookup"><span data-stu-id="6af1d-119">See Also</span></span>  
 [<span data-ttu-id="6af1d-120">ICLRErrorReportingManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6af1d-120">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [<span data-ttu-id="6af1d-121">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="6af1d-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
