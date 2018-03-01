---
title: "PublicKeyBlob 構造体"
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
- PublicKeyBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- PublicKeyBlob
helpviewer_keywords:
- PublicKeyBlob structure [.NET Framework strong naming]
ms.assetid: b9240712-829c-4c8d-9a09-a6e7aa63f63a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b1f04c692b7549c4d7d8d431591eeb867b673d9a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="cc9f7-102">PublicKeyBlob 構造体</span><span class="sxs-lookup"><span data-stu-id="cc9f7-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="cc9f7-103">公開/秘密キーのペアの公開キーをバイナリ形式で表します。</span><span class="sxs-lookup"><span data-stu-id="cc9f7-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc9f7-104">構文</span><span class="sxs-lookup"><span data-stu-id="cc9f7-104">Syntax</span></span>  
  
```  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a><span data-ttu-id="cc9f7-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="cc9f7-105">Members</span></span>  
  
|<span data-ttu-id="cc9f7-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="cc9f7-106">Member</span></span>|<span data-ttu-id="cc9f7-107">説明</span><span class="sxs-lookup"><span data-stu-id="cc9f7-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="cc9f7-108">署名アルゴリズムの識別子 (型の`ALG_ID`WinCrypt.h で定義されている、) の公開キー。</span><span class="sxs-lookup"><span data-stu-id="cc9f7-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="cc9f7-109">ハッシュ アルゴリズムの識別子 (型の`ALG_ID`WinCrypt.h で定義されている、) の公開キー。</span><span class="sxs-lookup"><span data-stu-id="cc9f7-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="cc9f7-110">(バイト単位)、キーの長さ。</span><span class="sxs-lookup"><span data-stu-id="cc9f7-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="cc9f7-111">CryptoAPI によって返される形式でキーの値を含む可変長バイト配列。</span><span class="sxs-lookup"><span data-stu-id="cc9f7-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc9f7-112">コメント</span><span class="sxs-lookup"><span data-stu-id="cc9f7-112">Remarks</span></span>  
 <span data-ttu-id="cc9f7-113">`PublicKeyBlob`構造体を使用して[StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)、 [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)、および公開/秘密キーのペアの公開キーを表すその他の厳密な名前の関数。</span><span class="sxs-lookup"><span data-stu-id="cc9f7-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc9f7-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="cc9f7-114">Requirements</span></span>  
 <span data-ttu-id="cc9f7-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cc9f7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc9f7-116">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="cc9f7-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="cc9f7-117">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="cc9f7-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cc9f7-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc9f7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc9f7-119">参照</span><span class="sxs-lookup"><span data-stu-id="cc9f7-119">See Also</span></span>  
 [<span data-ttu-id="cc9f7-120">StrongNameGetPublicKey 関数</span><span class="sxs-lookup"><span data-stu-id="cc9f7-120">StrongNameGetPublicKey Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)  
 [<span data-ttu-id="cc9f7-121">StrongNameSignatureGeneration 関数</span><span class="sxs-lookup"><span data-stu-id="cc9f7-121">StrongNameSignatureGeneration Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)  
 [<span data-ttu-id="cc9f7-122">厳密な名前付け構造体</span><span class="sxs-lookup"><span data-stu-id="cc9f7-122">Strong Naming Structures</span></span>](http://msdn.microsoft.com/library/4b041a2f-fd12-4b91-aacd-bc3b34a5124d)
