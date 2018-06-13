---
title: ICeeGen::GetSectionBlock メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionBlock
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionBlock
helpviewer_keywords:
- GetSectionBlock method [.NET Framework metadata]
- ICeeGen::GetSectionBlock method [.NET Framework metadata]
ms.assetid: 05c78aaf-5bbd-497e-9ae2-55f4fae0c5fb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5da2936a46dcf3d8f69acc3367db64712165b0cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444066"
---
# <a name="iceegengetsectionblock-method"></a>ICeeGen::GetSectionBlock メソッド
コード ベースのセクションのブロックを取得します。  
  
 このメソッドは、古いは使用できません。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetSectionBlock (  
    [in]  HCEESECTION    section,     
    [in]  ULONG          len,  
    [in]  ULONG          align     = 1,  
    [out] void           **ppBytes = 0  
);   
```  
  
#### <a name="parameters"></a>パラメーター  
 `section`  
 [in]コード ベースのブロックを取得する対象のセクションです。  
  
 `len`  
 [in]取得するブロックの長さ。  
  
 `align`  
 [in]ブロックの最初のバイトを配置に使用されたセクションの先頭からの相対バイト。 これは、セクション内のブロックの位置です。  
  
 `ppBytes`  
 [out]取得したブロックのアドレスを受け取る場所へのポインター。  
  
## <a name="remarks"></a>コメント  
 呼び出す`GetSectionBlock`他の方法で処理されない特別なセクションの要件がある場合にのみです。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICeeGen インターフェイス](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
