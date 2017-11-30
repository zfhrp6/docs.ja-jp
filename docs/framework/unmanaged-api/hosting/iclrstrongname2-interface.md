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
ms.openlocfilehash: 9e9a88f1064c888d60e363be569d06458299143d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="77941-102">ICLRStrongName2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="77941-102">ICLRStrongName2 Interface</span></span>
<span data-ttu-id="77941-103">Sha-2 グループ (sha-256、sha-384、および sha-512) のセキュリティで保護されたハッシュ アルゴリズムを使用する厳密な名前を作成する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="77941-103">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="77941-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="77941-104">Methods</span></span>  
  
|<span data-ttu-id="77941-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="77941-105">Method</span></span>|<span data-ttu-id="77941-106">説明</span><span class="sxs-lookup"><span data-stu-id="77941-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="77941-107">StrongNameGetPublicKeyEx メソッド</span><span class="sxs-lookup"><span data-stu-id="77941-107">StrongNameGetPublicKeyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamegetpublickeyex-method.md)|<span data-ttu-id="77941-108">公開/秘密キーのペアから公開キーを取得し、ハッシュ アルゴリズムと署名アルゴリズムを指定します。</span><span class="sxs-lookup"><span data-stu-id="77941-108">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="77941-109">StrongNameSignatureVerificationEx2 メソッド</span><span class="sxs-lookup"><span data-stu-id="77941-109">StrongNameSignatureVerificationEx2 Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamesignatureverificationex2-method.md)|<span data-ttu-id="77941-110">厳密な名前付きのアセンブリの署名を確認しの ECMA キーから実際のキーへのマッピングを提供します。</span><span class="sxs-lookup"><span data-stu-id="77941-110">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77941-111">コメント</span><span class="sxs-lookup"><span data-stu-id="77941-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77941-112">要件</span><span class="sxs-lookup"><span data-stu-id="77941-112">Requirements</span></span>  
 <span data-ttu-id="77941-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="77941-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77941-114">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="77941-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="77941-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="77941-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77941-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77941-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
