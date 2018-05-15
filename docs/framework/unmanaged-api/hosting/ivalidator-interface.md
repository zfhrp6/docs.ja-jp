---
title: IValidator インターフェイス
ms.date: 03/30/2017
api_name:
- IValidator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IValidator
helpviewer_keywords:
- IValidator interface [.NET Framework hosting]
ms.assetid: b297e3b0-20f9-478f-b707-5e2eecb2b5b2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e79a69bf71aee035fb1f9a0178879d7c19e62b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ivalidator-interface"></a><span data-ttu-id="12042-102">IValidator インターフェイス</span><span class="sxs-lookup"><span data-stu-id="12042-102">IValidator Interface</span></span>
<span data-ttu-id="12042-103">ポータブル実行可能 (PE) イメージを検証し、検証エラーを報告のメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="12042-103">Provides methods for validating portable executable (PE) images and reporting validation errors.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="12042-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="12042-104">Methods</span></span>  
  
|<span data-ttu-id="12042-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="12042-105">Method</span></span>|<span data-ttu-id="12042-106">説明</span><span class="sxs-lookup"><span data-stu-id="12042-106">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="12042-107">検証</span><span class="sxs-lookup"><span data-stu-id="12042-107">Validate</span></span>|<span data-ttu-id="12042-108">指定した PE または Microsoft intermediate language (MSIL) ファイルを検証します。</span><span class="sxs-lookup"><span data-stu-id="12042-108">Validates the specified PE or Microsoft intermediate language (MSIL) file.</span></span>|  
|<span data-ttu-id="12042-109">FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="12042-109">FormatEventInfo</span></span>|<span data-ttu-id="12042-110">指定された検証エラーに対応するエラー メッセージを取得します。</span><span class="sxs-lookup"><span data-stu-id="12042-110">Gets the error message corresponding to the specified validation error.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="12042-111">要件</span><span class="sxs-lookup"><span data-stu-id="12042-111">Requirements</span></span>  
 <span data-ttu-id="12042-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="12042-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12042-113">**ヘッダー:** IValidator.idl、IValidator.h</span><span class="sxs-lookup"><span data-stu-id="12042-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="12042-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="12042-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="12042-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12042-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12042-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="12042-116">See Also</span></span>  
 [<span data-ttu-id="12042-117">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="12042-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="12042-118">CorRuntimeHost コクラス</span><span class="sxs-lookup"><span data-stu-id="12042-118">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
