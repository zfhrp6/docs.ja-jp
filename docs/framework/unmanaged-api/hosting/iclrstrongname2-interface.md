---
title: "ICLRStrongName2 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName2
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName2
helpviewer_keywords: ICLRStrongName2 interface [.NET Framework hosting]
ms.assetid: 9f098a74-201e-4628-a468-8dee9ab99b4a
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d4e1274f675ae9289faa6c530d34cd61d033aa07
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="0d291-102">ICLRStrongName2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0d291-102">ICLRStrongName2 Interface</span></span>
<span data-ttu-id="0d291-103">Sha-2 グループ (sha-256、sha-384、および sha-512) のセキュリティで保護されたハッシュ アルゴリズムを使用する厳密な名前を作成する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="0d291-103">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0d291-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="0d291-104">Methods</span></span>  
  
|<span data-ttu-id="0d291-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="0d291-105">Method</span></span>|<span data-ttu-id="0d291-106">説明</span><span class="sxs-lookup"><span data-stu-id="0d291-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0d291-107">StrongNameGetPublicKeyEx メソッド</span><span class="sxs-lookup"><span data-stu-id="0d291-107">StrongNameGetPublicKeyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamegetpublickeyex-method.md)|<span data-ttu-id="0d291-108">公開/秘密キーのペアから公開キーを取得し、ハッシュ アルゴリズムと署名アルゴリズムを指定します。</span><span class="sxs-lookup"><span data-stu-id="0d291-108">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="0d291-109">StrongNameSignatureVerificationEx2 メソッド</span><span class="sxs-lookup"><span data-stu-id="0d291-109">StrongNameSignatureVerificationEx2 Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamesignatureverificationex2-method.md)|<span data-ttu-id="0d291-110">厳密な名前付きのアセンブリの署名を確認しの ECMA キーから実際のキーへのマッピングを提供します。</span><span class="sxs-lookup"><span data-stu-id="0d291-110">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d291-111">コメント</span><span class="sxs-lookup"><span data-stu-id="0d291-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d291-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="0d291-112">Requirements</span></span>  
 <span data-ttu-id="0d291-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0d291-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d291-114">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="0d291-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0d291-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="0d291-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d291-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d291-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
