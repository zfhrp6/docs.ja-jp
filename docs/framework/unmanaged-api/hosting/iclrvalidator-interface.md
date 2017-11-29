---
title: "ICLRValidator インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRValidator
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRValidator
helpviewer_keywords: ICLRValidator interface [.NET Framework hosting]
ms.assetid: 2edd0a10-77fb-4173-91eb-f2970cc364d0
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0057be1457ad369b84f311008180dc7c4a3c323d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrvalidator-interface"></a><span data-ttu-id="288b0-102">ICLRValidator インターフェイス</span><span class="sxs-lookup"><span data-stu-id="288b0-102">ICLRValidator Interface</span></span>
<span data-ttu-id="288b0-103">ポータブル実行可能 (PE) イメージを検証し、検証エラーを報告のメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="288b0-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="288b0-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="288b0-104">Methods</span></span>  
  
|<span data-ttu-id="288b0-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="288b0-105">Method</span></span>|<span data-ttu-id="288b0-106">説明</span><span class="sxs-lookup"><span data-stu-id="288b0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="288b0-107">FormatEventInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="288b0-107">FormatEventInfo Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-formateventinfo-method.md)|<span data-ttu-id="288b0-108">指定された検証エラーに関する詳細なメッセージを取得します。</span><span class="sxs-lookup"><span data-stu-id="288b0-108">Gets a detailed message about the specified validation error.</span></span>|  
|[<span data-ttu-id="288b0-109">Validate メソッド</span><span class="sxs-lookup"><span data-stu-id="288b0-109">Validate Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-validate-method.md)|<span data-ttu-id="288b0-110">ポータブル実行可能ファイルまたは Microsoft intermediate language (MSIL) で指定されたファイルを検証します。</span><span class="sxs-lookup"><span data-stu-id="288b0-110">Validates the portable executable or Microsoft intermediate language (MSIL) in the specified file.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="288b0-111">要件</span><span class="sxs-lookup"><span data-stu-id="288b0-111">Requirements</span></span>  
 <span data-ttu-id="288b0-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="288b0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="288b0-113">**ヘッダー:** IValidator.idl、IValidator.h</span><span class="sxs-lookup"><span data-stu-id="288b0-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="288b0-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="288b0-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="288b0-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="288b0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="288b0-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="288b0-116">See Also</span></span>  
 [<span data-ttu-id="288b0-117">ICLRErrorReportingManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="288b0-117">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [<span data-ttu-id="288b0-118">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="288b0-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="288b0-119">CLRRuntimeHost コクラス</span><span class="sxs-lookup"><span data-stu-id="288b0-119">CLRRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
