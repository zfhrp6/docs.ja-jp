---
title: ICeeGen::GetSectionDataLen メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionDataLen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionDataLen
helpviewer_keywords:
- ICeeGen::GetSectionDataLen method [.NET Framework metadata]
- GetSectionDataLen method [.NET Framework metadata]
ms.assetid: e2a06ee4-b8ee-49c7-935a-c1031a29eef2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b85cdee4a65e91c51fdb014bdcc4797b99214daf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446132"
---
# <a name="iceegengetsectiondatalen-method"></a>ICeeGen::GetSectionDataLen メソッド
指定されたセクションの長さを取得します。  
  
 このメソッドは、古いは使用できません。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `section`  
 [in]セクション「データの長さが取得されます。  
  
 `dataLen`  
 [out]指定されたセクションの返される長さ。  
  
## <a name="remarks"></a>コメント  
 呼び出す`GetSectionDataLen`他の方法で処理されない特別なセクションの要件がある場合にのみです。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICeeGen インターフェイス](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
