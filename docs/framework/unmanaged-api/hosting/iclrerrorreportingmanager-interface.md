---
title: ICLRErrorReportingManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager
helpviewer_keywords:
- ICLRErrorReportingManager interface [.NET Framework hosting]
ms.assetid: ea8af0d5-4133-4472-8a1f-50570d7e85fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf9e04ed1d3a68fed120c4c13ad992af1f777244
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433797"
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="b586c-102">ICLRErrorReportingManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b586c-102">ICLRErrorReportingManager Interface</span></span>
<span data-ttu-id="b586c-103">ホストがエラー報告用のカスタム スタック ダンプを設定できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="b586c-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b586c-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="b586c-104">Methods</span></span>  
  
|<span data-ttu-id="b586c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="b586c-105">Method</span></span>|<span data-ttu-id="b586c-106">説明</span><span class="sxs-lookup"><span data-stu-id="b586c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b586c-107">BeginCustomDump メソッド</span><span class="sxs-lookup"><span data-stu-id="b586c-107">BeginCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="b586c-108">エラー報告用にカスタム スタック ダンプの構成を指定します。</span><span class="sxs-lookup"><span data-stu-id="b586c-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="b586c-109">EndCustomDump メソッド</span><span class="sxs-lookup"><span data-stu-id="b586c-109">EndCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="b586c-110">事前に呼び出したによって設定されたカスタム スタック ダンプ構成をクリア`BeginCustomDump`です。</span><span class="sxs-lookup"><span data-stu-id="b586c-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="b586c-111">GetBucketParametersForCurrentException メソッド</span><span class="sxs-lookup"><span data-stu-id="b586c-111">GetBucketParametersForCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="b586c-112">呼び出し元のスレッドで現在の例外のワトソン バケットを取得します。</span><span class="sxs-lookup"><span data-stu-id="b586c-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b586c-113">コメント</span><span class="sxs-lookup"><span data-stu-id="b586c-113">Remarks</span></span>  
 <span data-ttu-id="b586c-114">`BeginCustomDump`メソッドは、カスタム スタック ダンプ構成を設定します。</span><span class="sxs-lookup"><span data-stu-id="b586c-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="b586c-115">`EndCustomDump`メソッドは、カスタム スタック ダンプ構成をクリアし、その関連付けられた状態を解放します。</span><span class="sxs-lookup"><span data-stu-id="b586c-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="b586c-116">これはカスタムのダンプの完了後に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="b586c-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b586c-117">呼び出しに失敗する`EndCustomDump`によってメモリ リークが発生します。</span><span class="sxs-lookup"><span data-stu-id="b586c-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b586c-118">要件</span><span class="sxs-lookup"><span data-stu-id="b586c-118">Requirements</span></span>  
 <span data-ttu-id="b586c-119">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b586c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b586c-120">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b586c-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b586c-121">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="b586c-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b586c-122">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b586c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b586c-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="b586c-123">See Also</span></span>  
 [<span data-ttu-id="b586c-124">ECustomDumpItemKind 列挙型</span><span class="sxs-lookup"><span data-stu-id="b586c-124">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)  
 [<span data-ttu-id="b586c-125">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b586c-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
