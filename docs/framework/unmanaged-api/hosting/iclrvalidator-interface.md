---
title: ICLRValidator インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRValidator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator
helpviewer_keywords:
- ICLRValidator interface [.NET Framework hosting]
ms.assetid: 2edd0a10-77fb-4173-91eb-f2970cc364d0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0cefd47d3c7298f9cc4b15eb2946f3d95aeae759
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438000"
---
# <a name="iclrvalidator-interface"></a><span data-ttu-id="42426-102">ICLRValidator インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42426-102">ICLRValidator Interface</span></span>
<span data-ttu-id="42426-103">ポータブル実行可能 (PE) イメージを検証し、検証エラーを報告のメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="42426-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="42426-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="42426-104">Methods</span></span>  
  
|<span data-ttu-id="42426-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="42426-105">Method</span></span>|<span data-ttu-id="42426-106">説明</span><span class="sxs-lookup"><span data-stu-id="42426-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="42426-107">FormatEventInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="42426-107">FormatEventInfo Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-formateventinfo-method.md)|<span data-ttu-id="42426-108">指定された検証エラーに関する詳細なメッセージを取得します。</span><span class="sxs-lookup"><span data-stu-id="42426-108">Gets a detailed message about the specified validation error.</span></span>|  
|[<span data-ttu-id="42426-109">Validate メソッド</span><span class="sxs-lookup"><span data-stu-id="42426-109">Validate Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md)|<span data-ttu-id="42426-110">ポータブル実行可能ファイルまたは Microsoft intermediate language (MSIL) で指定されたファイルを検証します。</span><span class="sxs-lookup"><span data-stu-id="42426-110">Validates the portable executable or Microsoft intermediate language (MSIL) in the specified file.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="42426-111">要件</span><span class="sxs-lookup"><span data-stu-id="42426-111">Requirements</span></span>  
 <span data-ttu-id="42426-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="42426-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42426-113">**ヘッダー:** IValidator.idl、IValidator.h</span><span class="sxs-lookup"><span data-stu-id="42426-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="42426-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="42426-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="42426-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42426-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42426-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="42426-116">See Also</span></span>  
 [<span data-ttu-id="42426-117">ICLRErrorReportingManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42426-117">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [<span data-ttu-id="42426-118">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42426-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="42426-119">CLRRuntimeHost コクラス</span><span class="sxs-lookup"><span data-stu-id="42426-119">CLRRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
