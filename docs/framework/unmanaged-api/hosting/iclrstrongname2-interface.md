---
title: ICLRStrongName2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRStrongName2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName2
helpviewer_keywords:
- ICLRStrongName2 interface [.NET Framework hosting]
ms.assetid: 9f098a74-201e-4628-a468-8dee9ab99b4a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bf9e3d2df8f507e118b393007c3958358a830cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="iclrstrongname2-interface"></a>ICLRStrongName2 インターフェイス
Sha-2 グループ (sha-256、sha-384、および sha-512) のセキュリティで保護されたハッシュ アルゴリズムを使用する厳密な名前を作成する機能を提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[StrongNameGetPublicKeyEx メソッド](../../../../docs/framework/unmanaged-api/hosting/strongnamegetpublickeyex-method.md)|公開/秘密キーのペアから公開キーを取得し、ハッシュ アルゴリズムと署名アルゴリズムを指定します。|  
|[StrongNameSignatureVerificationEx2 メソッド](../../../../docs/framework/unmanaged-api/hosting/strongnamesignatureverificationex2-method.md)|厳密な名前付きのアセンブリの署名を確認しの ECMA キーから実際のキーへのマッピングを提供します。|  
  
## <a name="remarks"></a>コメント  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]
